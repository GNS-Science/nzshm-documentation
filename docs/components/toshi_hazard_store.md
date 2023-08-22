# Toshi Hazard Store (Library)

A Python 3 library that defines the Dynamodb storage models and helper functions that can used to access to the NSHM Hazard model data stored in DynamoDB.

## Project Status

[![pypi](https://img.shields.io/pypi/v/toshi-hazard-store.svg)](https://pypi.org/project/toshi-hazard-store/)
[![python](https://img.shields.io/pypi/pyversions/toshi-hazard-store.svg)](https://pypi.org/project/toshi-hazard-store/)
[![Build Status](https://github.com/GNS-Science/toshi-hazard-store/actions/workflows/dev.yml/badge.svg)](https://github.com/GNS-Science/toshi-hazard-store/actions/workflows/dev.yml)
[![codecov](https://codecov.io/gh/GNS-Science/toshi-hazard-store/branch/main/graphs/badge.svg)](https://codecov.io/github/GNS-Science/toshi-hazard-store)


Used in ..

  - GNS-Science / nzshm-runzi
  
  - GNS-Science / toshi-hazard-haste
 
  - GNS-Science / toshi-hazard-post
 
  - GNS-Science / toshi-hazard-utils
 
  - GNS-Science / kororaa-graphql-api
 
 see https://github.com/GNS-Science/toshi-hazard-store/network/dependents
 
 ## PynamodB Models

```
    OpenquakeRealization
    ToshiOpenquakeMeta
    HazardAggregation
    GriddedHazard    
    DisaggAggregationExceedance
    DisaggAggregationOccurence
```

 ## Main Dependencies

See pyproject.toml

```
    openquake-engine
    numpy
    pandas
    pynamodb-attributes
    python
    nzshm-common
```
    