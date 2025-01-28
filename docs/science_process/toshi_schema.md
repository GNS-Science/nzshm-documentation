
## Toshi Hazard objects (Task + Solution + Config)
```mermaid

classDiagram
    
    
    class OHT["Openquake Hazard Task"] {
        <<AutomationTaskInterface, Node>>
        config "The task configuration"
        hazard_solution "The openquake solution"

        model_type enum CRUSTAL, SUBDUCTION, COMPOSITE
        task_type enum HAZARD, DISAGG, UNDEFINED
    }

    class OHS["Openquake Hazard Solution"] {
        <<PredecessorsInterface, Node>>
        created "When it was created UTZ"
        metrics "result metrics ...  a list of Key Value pairs."
        meta "metadata... a list of Key Value pairs."
        produced_by  "The task that produced this solution"
        task_args = "task arguments json file."

        config "the template configuration used to produce this solution"
        modified_config = "a zip archive containing modified config files."
        csv_archive = "zip archive containing hazard csv outputs `oq engine --export-outputs ....`"
        hdf5_archive "a zip of the raw hdf5"


    }


    class OHC["Openquake Hazard Config"] {
        <<Node>>
        nodeId[] source_models "List of Source NRML files"
        nodeId   template_archive "archive of all the additional config files"
    }

    OHT "*" -- "1" OHC
    OHS "*" -- "1" OHC
    OHT "1" -- "0..1" OHS

    note for OHS "T3BlbnF1YWtlSGF6YXJkU29sdXRpb246NjUzNjk0MQ=="
    note for OHT "T3BlbnF1YWtlSGF6YXJkVGFzazo2NTM2ODgx"

```

### crumbs
```
    class OHT1["Openquake Hazard Task from pres"] {
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
```