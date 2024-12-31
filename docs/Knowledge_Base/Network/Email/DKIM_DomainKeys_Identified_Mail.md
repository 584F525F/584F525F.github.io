!!! info ""

    ### Summary & Resources

    DomainKeys Identified Mail (DKIM) is a method of email authentication that helps prevent spammers and other malicious parties from impersonating a legitimate domain.

    - [dns-dkim-record](https://www.cloudflare.com/learning/dns/dns-records/dns-dkim-record/)
    - [Email Spoof Test](https://emailspooftest.com/)


!!! info ""

    ### How it works

    ![alt text](/Knowledge_Base/images/DKIM_Howitworks.png)


!!! info ""


    ### Example

    ```bash
    v=DMARC1; p=reject; rua=mailto:reportabuse@exampledomain.net; pct=100; adkim=s; aspf=s;

    v=DMARC1; p=reject; pct=100; adkim=s; aspf=s; rua=mailto:reportabuse@exampledomain.net; ruf=mailto:reportabuse@exampledomain.net; rf=afrf; ri=86400; fo=1_
    ```


!!! info ""

    ### Tags

    | TAG          | TAG DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | v (required) | The **version tag**. The only allowed value is "DMARC1". If it's incorrect or the tag is missing, the DMARC record will be ignored.                                                                                                                                                                                                                                                                                                                                            |
    | p (required) | The **DMARC policy**. Allowed values are "none", "quarantine", or "reject". The default is "none," which takes no action against non-authenticated emails. It only helps collect DMARC reports and gain insight into your current email flows and their authentication status. "quarantine" marks the failed emails as suspicious, while "reject" blocks them.                                                                                                                 |
    | rua          | **Aggregate report sending destination**. It's the "mailto:" URI that ESPs use to send failure reports. The tag is optional, but you won’t receive reports if you skip it.                                                                                                                                                                                                                                                                                                     |
    | ruf          | **Forensic (Failure) report sending destination**. It's the "mailto:" URI that ESPs use to send failure reports. The tag is optional, but you won’t receive reports if you skip it.                                                                                                                                                                                                                                                                                            |
    | sp           | **The subdomain policy**. The subdomain inherits the domain policy tag (p=) explained above unless specifically defined here. Like the domain policy, the allowed values are "none," "quarantine," or "reject." This option isn't widely used nowadays.                                                                                                                                                                                                                        |
    | adkim        | The **DKIM signature alignment**. This tag follows the alignment between the DKIM domain and the parent Header From domain. Allowed values are "r" (relaxed) or "s" (strict). "r" is the default and allows a partial match, while the "s" tag requires the domains to be the same.                                                                                                                                                                                            |
    | aspf         | **The SPF alignment**. This tag follows the alignment between the SPF domain (the sender) and the Header From domain. Allowed values are "r" (relaxed) or "s" (strict). "r" is the default, and allows a partial match, while the "s" tag requires the domains to be exactly the same.                                                                                                                                                                                         |
    | fo           | **Forensic reporting options**. Allowed values are "0," "1," "d," and "s." "0" is the default value, which generates a forensic report when both SPF and DKIM fail to produce an aligned pass. If either of the protocol outcome is something other than pass, use "1." "d" generates a report when DKIM is invalid, while "s" does the same for SPF. Define the ruf tag to receive forensic reports.                                                                          |
    | rf           | **The reporting format for failure reports**. Allowed values are "afrf" and "iodef".                                                                                                                                                                                                                                                                                                                                                                                           |
    | pct          | **The percentage tag**. This tag works on domains with "quarantine" or "reject" policy only. It marks the percentage of failed emails a given policy should be applied to. The rest falls under a lower policy. For example, if "pct=70," on a domain with "quarantine" policy, it applies only 70% of the time. The remaining 30% goes under "p=none". Similarly, if "p=reject" and "pct=70," "reject" applies to the 70% of failed emails, and the 30% go into "quarantine." |
    | ri           | **Reporting interval**. Marks the frequency of received XML reports in seconds. The default is 86400 (once a day). Regardless of the set interval, in most cases, ISPs send the reports at different intervals (usually once a day).                                                                                                                                                                                                                                           |
