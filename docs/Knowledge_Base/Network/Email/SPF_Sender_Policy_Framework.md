!!! info ""

    ### Summary & Resources

    sender policy framework (SPF) record is a type of DNS TXT record that lists all the servers authorized to send emails from a particular domain.

    - [DNS SPF record overview - Cloudflare](https://www.cloudflare.com/learning/dns/dns-records/dns-spf-record/)
    - [Open spf - SPF Record Syntax](http://www.open-spf.org/SPF_Record_Syntax/)
    - [Email Spoof Test](https://emailspooftest.com/)


!!! info ""

    ### How it works

    ![alt text](/Knowledge_Base/images/SPF_Howitworks.png)

    ---

    #### Mechanisms

    ```bash
    "+"	Pass
    "-"	Fail
    "~"	SoftFail
    "?"	Neutral
    ```

    #### The "all" mechanism

    Allow domain's MXes to send mail for the domain, prohibit all others

    ```bash
    v=spf1 mx -all
    ```

    The domain sends no mail at all
    
    ```bash
    v=spf1 -all
    ```

    The domain owner thinks that SPF is useless and/or doesn't care.

    ```bash
    v=spf1 +all
    ```

    Settings up a DNS record for SPF fail all that are not included

    ```bash
    spf
    Type: TXT
    Name: @
    Content: "v=spf1 include:_spf.mx.xyz.net -all"
    ```

!!! info ""

    ### Tools

    - [DMARCShield github](https://github.com/emenmousavi/DMARCShield) 
        DMARCShield is a Python program for email authentication and security. It offers a DMARC checker to ensure domain security, and a spoofing email sender to test for vulnerabilities. Protect your email communication and keep your domain safe with MailSecure.
