!!! info ""

    ```bash
    mirror 1 port (destination interface)
    interface (source interface) monitor all both mirror 1
    ```

    Example

    Mirroring Port F11 to Destination Port E4. Using Mirror 2, usually you will have multiple mirrors that you can setup, I configured mirror 2 in my case.

    ```bash
    mirror 2 port E4
    interface F11 monitor all both mirror 2
    ```
