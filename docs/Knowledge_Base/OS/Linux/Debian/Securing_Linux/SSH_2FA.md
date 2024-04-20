!!! info ""

    #### Installing and configuring required packages

    ```bash
    sudo apt install libpam-google-authenticator
    ```

!!! info ""

    #### Configuring SSH

    To make SSH use the Google Authenticator PAM module, add the following  line to the /etc/pam.d/sshd file

    ```bash
    auth required pam_google_authenticator.so
    ```

!!! info ""

    ### restart the sshd daemon

    ```bash
    sudo systemctl restart sshd.service
    ```

!!! info ""

    #### Modify /etc/ssh/sshd_config

    change ChallengeResponseAuthentication rom     no to yes
    so this part of the file looks like this:
    Change to yes to enable challenge-response passwords (beware issues with
      #some PAM modules and threads)
      ChallengeResponseAuthentication no #CHANGE THIS TO YES
      #Change to no to disable tunnelled clear text passwords
      #PasswordAuthentication yes

!!! info ""

    #### Configuring authentication

    ```bash
    google-authenticator
    ```

    It will ask you a series of questions (recommended configuration)

    ```bash
    Make tokens “time-base””: yes
    Update the .google_authenticator file: yes
    Disallow multiple uses: yes
    Increase the original generation time limit: no
    Enable rate-limiting: yes
    ```
    
    You will get secret key that you will then use to add to the Auth App

!!! info ""

    #### Adding the secret to Google Authenticator  

    ```bash
    Add to the Auth app
    type the secret key provided by google-authenticator command
    ```
