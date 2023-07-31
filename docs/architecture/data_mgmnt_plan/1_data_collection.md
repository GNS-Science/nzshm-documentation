 
## 1.1 Documentation and Metadata

### 1.1.1 What data will you collect or create?

??? note "Questions to consider:"

    What type, format and volume of data?
    
    Do your chosen formats and software enable sharing and long-term access to the data?
    Are there any existing data that you can reuse?
    
    Give a brief description of the data, including any existing data or third-party sources that will be used, in each case noting its content, type and coverage. Outline and justify your choice of format and consider the implications of data format and data volumes in terms of storage, backup and access.

The project will collect a large amount of primary data including, but not exclusively:

* Site characterization database
* Strong motion database
* Fault geometries
* Fault slip rates
* Earthquake catalogues
* Geodetic data
* Paleoseismic data

Primary data will be several GB in multiple formats. We will use easily read formats such as Excel, csv, and text files where possible.

Intermediate data products produced include:

* Earthquake rupture sets
* Rupture probabilities
* Ground motion models

Formats for intermediate data adhere to standards established by open source software used in the creation and analysis of the data such as [OpenQuake](https://github.com/gem/oq-engine) and [OpenSHA](https://opensha.org/) and will comprise many GB.

Final data products include:

* Seismic hazard probability curves
* Seismic hazard disaggregation matrices

Final data will be stored as entries in cloud databases. There will be several TB of final data products.

### 1.1.2 How will the data be collected or created?

??? note "Questions to consider:"

    What standards or methodologies will you use?
    How will you structure and name your folders and files?
    How will you handle versioning?
    What quality assurance processes will you adopt?
    Outline how the data will be collected/created and which community data standards (if any) will be used. Consider how the data will be organized during the project, mentioning for example naming conventions, version control and folder structures. Explain how the consistency and quality of data collection will be controlled and documented. This may include processes such as calibration, repeat samples or measurements, standardized data capture or recording, data entry validation, peer review of data or representation with controlled vocabularies.

Data will be collected via a diverse set of methods including field studies, geodetic surveys, retrieval of waveforms and earthquake catalogues from [GeoNet](https://www.geonet.org.nz/). Intermediate and final products are produced using publicly available software [OpenQuake](https://github.com/gem/oq-engine) and [OpenSHA](https://opensha.org/)  and [in-house developed software](https://github.com/GNS-Science) all available under open source licenses.