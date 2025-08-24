# nzshm-model

[![pypi](https://img.shields.io/pypi/v/nzshm-model.svg)](https://pypi.org/project/nzshm-model/)
[![python](https://img.shields.io/pypi/pyversions/nzshm-model.svg)](https://pypi.org/project/nzshm-model/)
[![Build Status](https://github.com/GNS-Science/nzshm-model/actions/workflows/dev.yml/badge.svg)](https://github.com/GNS-Science/nzshm-model/actions/workflows/dev.yml)
[![codecov](https://codecov.io/gh/GNS-Science/nzshm-model/branch/main/graphs/badge.svg)](https://codecov.io/github/GNS-Science/nzshm-model)

The logic tree definitions, final configurations, and versioning of the New Zealand | Aotearoa National Seismic Hazard Model are stored here.

## Links

 - [Github: GNS-Science/nzshm-model](https://github.com/GNS-Science/nzshm-model)
 - [Documentation](https://gns-science.github.io/nzshm-model/)
 - [PyPI: nzshm-model](https://pypi.org/project/nzshm-model/)
 - [Dependent projects](https://github.com/GNS-Science/nzshm-model/network/dependents)

## Features

 - Iterate the available NSHM models.
 - Iterate the components, or Logic Tree Branches (LTBs) for each model.
 - A branch component registry for unique, compact string ids for all the available LTBs.
 - Build job configurations for the OpenQuake PSHA engine, based on a given NSHM model or part(s) thereof.
