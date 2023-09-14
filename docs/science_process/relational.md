# NZSHM-Model relationships

## nzshm-model etc

```mermaid

classDiagram
    
    class Model["National Seismic Hazard Model (Model)"] {
        String version
        +get_version() : String
    }

    class SLT["Source Logic Tree (SLT)"] {
        Path python_source
        Path json_file
    }

    class SLTWC["SLT Weighted Component"] {
        +float weight 
    }


    class SLTC["SLT Component"] {
        +ToshiID inv_id
        +ToshiID bg_id
    }

    class GMCM_LT["Ground Motion Characteristic Model Logic Tree (GMCM_LT)"] {
        <<XML>>
        Path xml_source
    }

    class GMCM_LTB["GMCM_LT Branch"] {
        +Float weight
        +string gmm_id
    }


    Model "0..*" -- "1" SLT
    Model "0..*" -- "1" GMCM_LT
    SLT *-- SLTWC
    SLTWC "*" -- "1" SLTC
    GMCM_LT *-- GMCM_LTB 
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

    note for OHC "
    source_models  = List of Source NRML files
    template_archive = archive of all the configuration files besides those in source_models"
```

## OQ hazard processing

```mermaid

classDiagram
    
    direction TB

    class Model["Model"] {
    }

    class SLT["SLT"] {
    }

    class SLTC["SLT Component"] {
    }

    class GMCM_LT["GMCM_LT"] {
    }
   
    class GMCM_LTB["GMCM_LT Branch"] {
        Float weight
        string gmm_id
    }

    class OHT["Openquake Hazard Task/Solution"] {
        %% Toshi hazard task ID (e.g T3…)
        %% inv ID, bg ID (SLT comp branch)
        %% GMCM LT (in the template)
        %% IMTs
        %% OQ configs (e.g. vs30, oq settings, etc)
        %% Template (toshi ID)
        float vs30
        String[] imts
        String[] locations
        path openquake_settings
    }

    class HDF5["Openquake_HDF5"] {
        <<File>>
        realizations
        hazard_curves
    }

    class THS_meta["THS_OpenquakeMeta-PROD"] {
        <<DynamoDB Row>>
        String toshi_hazard_solution_id
    }

    class THS["THS_OpenquakeRealization-PROD"] {
        <<DynamoDB Row>>
        String toshi_hazard_solution_id
        String location_code
        Integer rlz_id
        Integer vs30
    }

    class RLZ["Realization"] {
        Integer id
    }

    Model "1..*" -- "1" SLT
    SLT "1" -- "1..*" SLTC
    Model "1..*" -- "1" GMCM_LT
 
    %% SLTC_VL -- OHT
    %% SLTC_VL "1..*" -- "1" SLTC
    GMCM_LT "1" -- "1..*" OHT
    SLTC "1" -- "1..*" OHT
    GMCM_LT "1" -- "1..*" GMCM_LTB 
    OHT "1" -- "1..*" THS
    OHT -- THS_meta
    RLZ "1" -- "1..*" THS

    SLTC -- RLZ
    GMCM_LTB -- RLZ

    HDF5 -- THS_meta
    HDF5 "1" -- "*" RLZ

    OHT --|> "produces" HDF5
```

## Not needed

```
    class SLTC_VL["SLTC_VS30_Location"] {
        +Int vs30
        +String location_code
    }

```