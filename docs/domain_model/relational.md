# NZSHM-Model relationships

This is parked, it contains some developmental diagrams used to infotm the wider class modelling.

## Toshi Hazard objects (Task + Solution + Config)

```mermaid
classDiagram
    
    %% direction LR
    class OpenquakeHazardSolution {
        <<Node>>
        String id: 
        String produced_by:
        config
        template
        File hazard_solution_csv_archive
        File hazard_solution_hdf5_archive
        
    }

    class OpenquakeHazardTask {
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
    
    class OpenquakeHazardConfig {
        <<Node>>
        Node[] source_models 
        template_archive
    }

    OpenquakeHazardTask "*" -- "1" OpenquakeHazardConfig
    OpenquakeHazardTask "1" -- "0..1" OpenquakeHazardSolution

    note for OpenquakeHazardSolution "T3BlbnF1YWtlSGF6YXJkU29sdXRpb246NjUzNjk0MQ=="
    note for OpenquakeHazardTask "T3BlbnF1YWtlSGF6YXJkVGFzazo2NTM2ODgx"
    
```

## OQ hazard processing

```mermaid
classDiagram
    
    direction TB

    class SourceLogicTreeBranch
    class GroundMotionLogicTreeBranch

    class OpenquakeHazardSolution {
        vs30
    }

    class THS_OpenquakeMeta {
        <<DynamoDB Row>>
        String toshi_hazard_solution_id
        etc
    }

    class THS_OpenquakeRealization {
        <<DynamoDB Row>>
        toshi_hazard_solution_id
        location_code
        rlz_id
        vs30
        hazard_curves
    }

    class Realization {
        Integer id
        string[] imts
        float[] poes
    }


 
    THS_OpenquakeRealization -- THS_OpenquakeMeta
    THS_OpenquakeRealization *-- Realization

    Realization "1" -- "1..*" OpenquakeHazardSolution

    SourceLogicTreeBranch -- Realization
    GroundMotionLogicTreeBranch -- Realization


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