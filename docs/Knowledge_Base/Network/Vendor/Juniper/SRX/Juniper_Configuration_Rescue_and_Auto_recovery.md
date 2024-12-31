!!! warning ""

    #### Why configuring this is important you say? 
    During the boot process, the device is configured based on a predefined configuration file. The device selects the configuration file based on the sequence shown below

    ![juni_config_1](/Knowledge_Base/images/juni_config_1.png)

!!! info ""

    #### the solution

    To show you current system alarms run

    ```bash
    show system alarms
    ```

    If you see the 2 Minor alarms then proceed with the next step

    ![juni_config_2](/Knowledge_Base/images/juni_config_2.png)

    You will need to run the following commands

    ```bash
    request system configuration rescue save
    request system autorecovery state save
    ```

    ![juni_config_3](/Knowledge_Base/images/juni_config_3.png)

    Once done executing the commands then check for alarms again by running 

    ```bash
    show system alarms
    ```

    ![juni_config_4](/Knowledge_Base/images/juni_config_4.png)
