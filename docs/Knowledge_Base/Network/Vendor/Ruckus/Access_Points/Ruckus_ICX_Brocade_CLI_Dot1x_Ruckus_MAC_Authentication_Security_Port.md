!!! info ""

    http://docs.ruckuswireless.com/fastiron/08.0.60/fastiron-08060-securityguide/GUID-173BF914-D248-4CAE-9D80-B036E8EC54E6.htmlhttp://docs.ruckuswireless.com/fastiron/08.0.60/fastiron-08060-securityguide/GUID-173BF914-D248-4CAE-9D80-B036E8EC54E6.html

    ```bash
    conf t
    authentication
    no mac-authentication enable ethernet 1/1/X
    exit
    no dot1x enable ethernet 1/1/X
    wr mem
    ```

    Check `Show run`, now you can untag VLAN to Port.
