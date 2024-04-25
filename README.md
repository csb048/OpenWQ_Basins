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

## Common Configuration Issues

### OpenWQ
- If your `OpenWQ` output for each time-step does not match the number of HRUs inputed. Check `openWQ_master.json`, there is a section titled `COMPARTMENTS_ANS_CELLS`.  If you are running `summa_openWQ` you will want it to look like this ...

    ```
    "COMPARTMENTS_AND_CELLS":{
        "SCALARAQUIFER":{  // Compartment for Summa
            "1": ["all",1,1]
        }			
    },
    ```
    
    And for `mizuroute_openWQ` you will want it to look like this...
    
    ```
    "COMPARTMENTS_AND_CELLS":{
        "RIVER_NETWORK_REACHES":{  // Compartment for Mizuroute
            "1": ["all",1,1]
        }			
    },
    ```
    This will allow `OpenWQ` to output the correct number of HRUs for each time-step.

### Mizuroute

- In `mizuroute.control` there are some deprecated vallues in the older versions of the config file. For example...
    
    ```
     FATAL ERROR: prep_output/Accepted <newFileFrequency> options (case-insensitive): single yearly, monthly, or daily
    ```
    This can be fixed by updating the `<newFileFrequency>` to one of the sudgested values in the error message. 
    
    From this ...
    
    ```
    <newFileFrequency>      annual                  ! Frequency for new output files (single, day, month, or annual) 
    ```
    To this ...
    
    ```
    <newFileFrequency>      yearly                  ! Frequency for new output files (single, day, month, or annual) 
    ```

- Another deprecated value is `<route_opt>`, when set to a unsupported value it throws an error

    ```
     FATAL ERROR: main_routing/only the routing methods listed below are supported in the mizuroute-openwq coupling: muskingumCunge (route_opt=4) and diffusiveWave (route_opt=5)
    ```
    Like the first problem, update ```<route_opt>``` to a supported value provided by the error message

### Summa

### Addtional Infomation
A trac ticket related to this can be found below.

https://simcity.usask.ca/trac/ticket/3341#comment:1

