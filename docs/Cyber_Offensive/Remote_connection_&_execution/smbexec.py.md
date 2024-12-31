!!! info ""

    A similar approach to PSEXEC w/o using RemComSvc. The technique is described [here](https://web.archive.org/web/20140625065218/http://blog.accuvant.com/rdavisaccuvant/owning-computers-without-shell-access/). Our implementation goes one step further, instantiating a local smbserver to receive the output of the commands. This is useful in the situation where the target machine does NOT have a writeable share available.

    ```shell
    # smbexec
    # A similar approach to PSEXEC w/o using RemComSvc. The technique is described here. 
    # Instantiating a local smbserver to receive the output of the commands. 
    # This is useful in the situation where the target machine does NOT have a writeable share available.
    smbexec.py domain/user:password@IP <command>
    ```
