# NZSHM-Model relationships

## nzshm-model etc

```mermaid

classDiagram
    
    class Model["SeismicHazardModel"] {
        string version
        string notes        
        date created
    }

    class SLT["SourceLogicTree"] {
        string version
        string notes
    }

    class SLTG["SourceLogicTreeGroup"] {
        string group e.g `Hik, Puy`
        string tectonic_region e.g. `Slab, Crustal`
    }

    class SLTB["SourceLogicTreeBranch"] {
        float weight
        string tag e.g. `Hik TL, N16.5, b0.95, C4, s0.42`
    }

    class SLTF["SourceLogicTreeSource"] {
        string source_id
        string tag e.g. `Hik TL, N16.5, b0.95, C4, s0.42, IFM`
    }

    class GMM_LT["GroundMotionModelLogicTree"] {
        string version
        string notes
    }   

    class GMM_LTB["GroundMotionModelLogicTreeBranch"] {
        float weight
        string args
        string tag e.g. BSSA-2014
    }

    class GMPE["GroundMotionPredictionEquation"] {
        string name e.g. Stirling 2015
        string[] tectonic_regions e.g. [`Slab, Crustal`]
        string repository/class
    }

    Model "0..*" -- "1" SLT
    Model "0..*" -- "1" GMM_LT
    SLT *-- "1..*" SLTG
    SLTG *-- "1..*" SLTB

    SLTB "0..*" -- "1..*" SLTF
    GMM_LT *-- "1..*" GMM_LTB 
    GMM_LTB "0..*" --"1" GMPE
```

## Toshi Hazard objects (Task + Solution + Config)

[see here](./toshi_schema)

```mermaid

classDiagram
    
    %% direction LR
    class OHS["Openquake Hazard Solution"] {
        <<Node>>
        String id: 
        String produced_by:
        config
        template
        File hazard_solution_csv_archive
        File hazard_solution_hdf5_archive
        
    }

    class OHT["Openquake Hazard Task"] {
        <<Node>>
        String id: 
        node hazard_solution
        model_type
        logic_tree_permutations
        intensity_spec
        vs30
        String[] location_list
        node template_archive
        hazard_config
        source_models
    }
    
    class OHC["OpenquakeHazardConfig"] {
        <<Node>>
        Node[] source_models 
        template_archive
    }

    OHT "*" -- "1" OHC
    OHT "1" -- "0..1" OHS

    note for OHS "T3BlbnF1YWtlSGF6YXJkU29sdXRpb246NjUzNjk0MQ=="
    note for OHT "T3BlbnF1YWtlSGF6YXJkVGFzazo2NTM2ODgx"
    
```

## OQ hazard processing

```mermaid

classDiagram
    
    direction TB

    class SLTC["SourceLogicTreeBranch"]   
    class GMCM_LTB["GroundMotionLogicTreeBranch"]

    class OHT["Openquake Hazard Solution"] {
        vs30
    }

    
    class THS_meta["THS_OpenquakeMeta-PROD"] {
        <<DynamoDB Row>>
        String toshi_hazard_solution_id
        etc
    }

    class THS["THS_OpenquakeRealization-PROD"] {
        <<DynamoDB Row>>
        toshi_hazard_solution_id
        location_code
        rlz_id
        vs30
        hazard_curves
    }

    class RLZ["Realization"] {
        Integer id
        string[] imts
        float[] poes
    }


 
    OHT -- THS_meta
    OHT *-- RLZ

    RLZ "1" -- "1..*" THS

    SLTC -- RLZ
    GMCM_LTB -- RLZ


```

## Not needed

```
    %% HDF5 -- THS_meta
    %% HDF5 "1" -- "*" RLZ

    %% OHT --|> "produces" HDF5
    class HDF5["Openquake_HDF5"] {
        <<File>>
        realizations
        hazard_curves
    }
    class SLTC_VL["SLTC_VS30_Location"] {
        +Int vs30
        +String location_code
    }

```