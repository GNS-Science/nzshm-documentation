## 4. Storage and Backup 

### 4.1 How will the data be stored and backed up during the research?

??? note "Questions to consider:"

    Do you have sufficient storage or will you need to include charges for additional services?
    How will the data be backed up?
    Who will be responsible for backup and recovery?
    How will the data be recovered in the event of an incident?
    State how often the data will be backed up and to which locations. How many copies are being made? Storing data on laptops, computer hard drives or external storage devices alone is very risky. The use of robust, managed storage provided by university IT teams is preferable. Similarly, it is normally better to use automatic backup services provided by IT Services than rely on manual processes. If you choose to use a third-party service, you should ensure that this does not conflict with any funder, institutional, departmental or group policies, for example in terms of the legal jurisdiction in which data are held or the protection of sensitive data.

Storage of data products will be provided by cloud-based object and database storage which includes regular backup schedules. Software developed to process data will be stored in cloud-based, version controlled [repositories](https://github.com/GNS-Science)

### 4.2 How will you manage access and security?

??? note "Questions to consider:"

    What are the risks to data security and how will these be managed?
    How will you control access to keep the data secure?
    How will you ensure that collaborators can access your data securely?
    If creating or collecting data in the field how will you ensure its safe transfer into your main secured systems?
    If your data is confidential (e.g. personal data not already in the public domain, confidential information or trade secrets), you should outline any appropriate security measures and note any formal standards that you will comply with e.g. ISO 27001.

Access to cloud storage services is controlled by accounts using multi-factor-authentication. The top-level account is controlled by GNS Science IT group and administrative access given to a small number of NSHM team members.

Access to data is controlled via several APIs developed for the project which use secret keys to specify level of access to data (e.g., read/write or read only).