!!! info ""

    #### Summary
    
    YARA is a tool aimed at (but not limited to) helping malware researchers to identify and classify malware samples. With YARA you can create descriptions of malware families (or whatever you want to describe) based on textual or binary patterns. [yara](https://yara.readthedocs.io/en/latest/)

    #### Resources

    - [Yara Binaries](https://github.com/VirusTotal/yara/releases)
    - [Yara Readthedocs](https://yara.readthedocs.io/en/stable/)
    - [Yara Git Repo](https://github.com/VirusTotal/yara)
    - [Kaspersky Yara Webinar](https://securelist.com/yara-webinar-follow-up/96505/)
    - [yaraPCAP](https://github.com/kevthehermit/YaraPcap)
    - [Kaspersky Klara](https://github.com/KasperskyLab/klara)
    - [YarGen](https://github.com/Neo23x0/yarGen)
    - [YARA Documentation](https://yara.readthedocs.io/en/stable/)
    - [VirusTotal/yara](https://virustotal.github.io/yara/)
    - [InQuest/awesome-yara](https://github.com/InQuest/awesome-yara)

    #### Example

    YARA is invoked with the command `yara64` in the newer version of FLARE-VM. If you can't run YARA by running `yara32`, try `yara64` instead!

    `-w` supress any errors
    `-p 32` number of threads threads
    `-s' print the matching strings defined in the template
    `-r` recurse directory

    ![alt text](/Knowledge_Base/images/PMT-img-yara-98dy-0.png)


