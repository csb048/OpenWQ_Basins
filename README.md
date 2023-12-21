# OpenWQ_Basins

These are the shapefiles for creating the input into SUMMA and Mizuroute for the OpenWQ project.

- Great_Slave_Lake:
  - This is just the Great Slave Lake Basin. This is unused but was the first set of shapefiles generated.

- Athabasca_River_and_Great_Slave_Lake:
  - These are the files that created the domain that is being used for runs. It contains both the Athabasca River Basin and the Great Slave Lake Basin totaling over 20,000 HRUs.

- Baker Creek Basin: 
    - This is the Baker Creek Basin. It is a small basin that is used for testing purposes.

# Configuration Files
 
These are the config files made for specific domains to be ran by summa-openwq and mizuroute-openwq.

- Great Slave Lake config:
    - This is where summa-openwq and mizuroute-openwq config files for the Great Slave Lake domain can be found.
        - Mizuroute_Settings: Contains the config files specificly for running mizuroute-openwq on this domain.
        - Summa_Settings: Contains the config files specificly for running summa-openwq on this domain.
    - **NOTE:** Remember to modify mizuroute.control and fileManager.txt with updated paths for input and output dirrectories, and update the paths in openWQ_master.json for the additional openwq config files.  For best reults use absolute paths.  
