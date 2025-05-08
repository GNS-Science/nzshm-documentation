???+ warning "Nov 2023 - this is model under active revision !!"

## Introduction

These are databases of related hazard curves each associated with a specific combination of Sources and GMMs.


## Seismic Hazard Model diagram



```mermaid
classDiagram
direction LR

class HazardModelRealisation {
    vs30s() integer
    LocationList() string[]
    IMTList() string[]
    hazardCurve(vs30, IMT, Location)
}

class HazardCurveResult {
    vs30() string
    Location() string
    IMT() string
    curves() float[]
}

SeismicHazardModel -- "0..*" HazardModelRealisation
HazardModelRealisation -- "0..*" HazardCurveResult
```

???+ "Accessing the NSHM hazard realisations" 

    The NZ NSHM project makes Hazard Model Realisations available via a graphql web API. There is also a python client library that wraps the web API and also allows the user to cache results locally for better performance in many situations.

