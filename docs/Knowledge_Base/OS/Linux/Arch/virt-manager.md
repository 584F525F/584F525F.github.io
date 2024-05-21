!!! error ""

	### virt manager: "network 'default' is not active"
	
	List the available network

	```bash
	sudo virsh net-list --all
	```
	
	In my case it was default, change default if your is different
	
	```bash
	sudo virsh net-start default
	```

	You can create a .sh script with the net-start and have it run on boot up.	
	

!!! info ""

	### share clipboard
	
    Must have installed the following on host and agent > spice-vdagent
	enable shared memory on VM
	
    ```bash
    systemctl enable spice-vdagentd.service
	systemctl start spice-vdagentd.service
    ```

	Create shared folder for vm in virt manager
	Add hardware > Filesystem > Driver virtiofs
	set a source path and target path
	
    ```bash
    Example source path: /home/penguin/Desktop/VM-share/
	Example Target Path: my-vm-share
    ```

	Boot Options > Checked the Auto Start
	Make sure the VirtIO Disk is checked

	On host do the below
	
    ```bash
    sudo gedit /etc/xdg/autostart/spice-vdagent.desktop

    If you use KDE guest, just remove the line X-GNOME-Autostart-Phase=WindowManager in it. Then reboot.
    ```
	
    pacman will overwrite it back when update or reinstall spice-vdagent.

	There are possible two solutions:
	    1- You can create a separate same file in ~/.config/autostart/spice-vdagent.desktop

	    2- Edit /etc/pacman.conf to add

        ```bash
        NoUpgrade = etc/xdg/autostart/spice-vdagent.desktop
        ```


!!! info ""

	### Enable multiple screens	
	
	```bash
	Video QXL > edit the XML part of the in the QEMU machine profile to say “heads=2” instead of “heads=1”, looks something like this

	<video>
	  <model type="qxl" ram="65536" vram="65536" vgamem="16384" heads="2" primary="yes"/>
	  <alias name="video0"/>
	  <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x0"/>
	</video>
	```bash

	install virt-viewer

	```bash
	sudo pacman -S virt-viewer
	```

	to run a vnc session [change the 5900 to the port number you selected]

	```bash
	remote-viewer spice://localhost:5900
	```

	Select display 1 & 2, etc...


!!! info ""

	### screen auto resize fix
	
	install Windows spice agent [spice-space](https://www.spice-space.org/download.html)
	
	Windows binaries section > Windows SPICE Guest Tools (spice-guest-tools)
	
	[Windows SPICE Guest Tools binary](https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe)
	
	Run the binary on your Windows machine, once done go to the virt manager tool bar
	View > Scale Display > check the "Auto resize VM with window"
	Now you should be able to see it working as expected

!!! info ""

    ### Installing windows 11 steps on virt manager

    https://sysguides.com/install-a-windows-11-virtual-machine-on-kvm


!!! info ""

	Resources

	[install-virtio-drivers-for-windows-guests](https://sysguides.com/install-kvm-on-linux#3-04-install-virtio-drivers-for-windows-guests-)
	[mount-the-virtio-winiso-image](https://sysguides.com/install-a-windows-11-virtual-machine-on-kvm#6-16-mount-the-virtio-winiso-image)