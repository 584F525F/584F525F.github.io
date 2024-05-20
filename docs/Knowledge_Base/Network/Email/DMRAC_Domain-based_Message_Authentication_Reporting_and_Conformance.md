!!! info ""

    ### Summary & Resources

    Domain-based Message Authentication Reporting and Conformance (DMARC) is a method of authenticating email messages. A DMARC policy tells a receiving email server what to do after checking a domain's Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM) records, which are additional email authentication methods.

    - [DNS DMARC record summary - Clopudflare](https://www.cloudflare.com/learning/dns/dns-records/dns-dmarc-record/)
    - [DMARC org](https://dmarc.org/)


!!! info ""

    ### How it works

    ![alt text](/Knowledge_Base/images/DMARC_Howitworks.png)

    ![alt text](/Knowledge_Base/images/DMARK_Record_Syntax.png)

    Settings up a DNS record for DMARC with all rejects. multiple types of content text provided

    ```bash
    Type: TXT
    Name: _dmarc
    Content: "v=DMARC1; p=reject; pct=100"
    Content: "v=DMARC1; p=reject; pct=100; adkim=s; aspf=s"
    Content: "v=DMARC1; p=reject; pct=100; adkim=s; fo=1; aspf=s; rua=mailto:report@mydomain.com,mailto:report@xyz.com"
    ```
