!!! failure ""

    #### the error message

    WLC error log message: _*spamApTask6:  %DTLS-3-HANDSHAKE_FAILURE: openssl_dtls.c:844 Failed to complete DTLS handshake with peer_

    or:

    _Failed to complete DTLS handshake with peer 10.32.41.96 for AP 00:1d:45:36:97:30_   
    _*spamReceiveTask: Sep 19 21:42:59.855: %DTLS-3-HANDSHAKE_FAILURE: openssl_dtls.c:631 Failed to complete DTLS handshake with peer 1.2.3.4 for AP 00:11:22:33:44:55_

!!! info ""

    #### explanation

    By default, if an AP and/or WLC certificate has expired, then the DTLS connection will fail. To get around this we had to enable a command in the WLC that ignored the AP cert. The happened because the Manufacturer Installed Certificate (MIC) has now become older than ten years and has expired. To allow AP’s to join a WLC after certificate expiration, upgrade to the fixed software version, then use the following commands:

    ```bash
    ! For 7.0.252.0:
    (WLC)>config ap lifetime-check {mic|ssc} enable
    ! For 7.4.140.0 and later:
    (WLC)>config ap cert-expiry-ignore {mic|ssc} enable
    ```

    With ```config ap lifetime-check {mic|ssc} enable``` or ```config ap cert-expiry-ignore {mic|ssc} enable``` in effect, the WLC and AP will ignore the expiration date on the devices’ MICs and SSCs.
    
    The above-noted commands must remain in effect as long as devices with expired MIC or SSC certificates are used.

!!! success ""

    #### Solution

    SSH into the WLC and run the following commands:

    ```bash
    !on WLC 8.x:
    config ap cert-expiry-ignore mic enable
    config ap cert-expiry-ignore ssc enable
    config ap dtls-cipher-suite RSA-AES128-SH
    config ap dtls-wlc-mic sha2
    !on WLC 7.x:
    config ap lifetime-check mic enable
    config ap lifetime-check ssc enable
    ```

    if that doesn’t help try

    ```bash
    config auth-list ap-policy ssc enable
    config certificate ssc hash validation disable
    ```
