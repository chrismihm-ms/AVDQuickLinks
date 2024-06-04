# Linux Support and Common Deployment Patterns
*All of the info below can be referenced from John Kelbley's blog article: [Secure Linux Access Using Azure Virtual Desktop](https://techcommunity.microsoft.com/t5/azure-architecture-blog/secure-linux-access-using-azure-virtual-desktop/ba-p/3793575)*

A deployment pattern growing in popularity is to publish access to Linux resources via AVD.  The AAD requirement for AVD is a perfect security wrapper for many dev and test Linux deployments, since it creates a security wrapper for those environments which might otherwise be challenging to implement (example:  where devs want to manage passwords on their own Linux machines!). Currently Linux Azure Virtual Desktop session hosts aren't support at the moment. Here are some alternatives to provide a Linux experience in AVD.
 
The common emerging patterns we have seen for secure Linux access using AVD include:
- Install Linux on Windows with WSL
- Install links on VDI that enables remote access to Linux VM 
- Publish Linux Desktop via AVD RemoteApp:
  - Telnet (PuTTY, MobaXterm, other)
  - Xrdp access either with MSTC or MobaXterm
  - X11 access using X2go
  
  
*[Quick Reference to Configuring single sign-on for AVD](https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-single-sign-on)*

## Install Linux on Windows with WSL
Enabling the Windows Subsystem for Linux (WSL) in AVD lets developers install a Linux distribution (such as Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc) and use Linux applications, utilities, and Bash command-line tools directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup. This setup would require the AVD user to have a dedicated/persistent desktop (Cannot use Multi-Session hosts).

- [Windows Subsystem for Linux Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
- [Install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

## Install links on VDI that enables remote access to Linux VM 
This option requires you to create a Linux VM in Azure with the appropriate applications installed. The VM should be created without a public IP and with networking line of site to the virtual desktops in the AVD deployment.On the AVD virtual desktop, install a link that enables remote access to the Linux system and appropriate applications.

## Publish Linux Desktop via AVD RemoteApp
With this option, you will publish the application used to remotely access the Linux VM as a Remote Application – when the customer clicks on the Remote Application, they are redirected to the Linux-based system. AVD lets you publish either individual applications (Remote Apps) or the full Windows desktop experience.

AVD lets you publish either individual applications (Remote Apps) or the full Windows desktop experience:  
![RemoteApp Options](/Diagrams/remote_app_1.jpg)  

### PuTTY – Easy (if you don’t need GUI!
PuTTY is well known to your Linux users (I’ll bet, and super easy to install / publish via RemoteApp!).
Once it’s deployed, just share the IP address(es) of the hosts your users need access to, and they can setup the “saved sessions”:  
![Putty RemoteApp](/Diagrams/putty_remote_app_1.jpg)  
![Putty RemoteApp](/Diagrams/putty_remote_app_2.jpg) 

### Xrdp with MSTSC
Let's look at that Ubuntu Icon in the Remote Desktop application.  
  
While it is implemented as a Remote Application (our old friend MSTSC) it publishes a full Ubuntu desktop:  
![Xrdp RemoteApp](/Diagrams/xrdp_w_mstsc_1.jpg)  
  
When the user clicks on it, they get the familiar connection dialog:  
![Xrdp RemoteApp](/Diagrams/xrdp_w_mstsc_2.jpg)  
  
...and maybe that secondary authentication prompt for Windows  
(again, this can be eliminated if you implement single sign on:)  
![Xrdp RemoteApp](/Diagrams/xrdp_w_mstsc_3.jpg)  
 
BUT THEN they get to their Linux desktop:  
![Xrdp RemoteApp](/Diagrams/xrdp_w_mstsc_4.jpg)  
In this case, it's an xrdp login prompt for a local credential stored in etc/passwd (could also be PAM integrated).  
  
Once they log in - they have their desktop:  
![Xrdp RemoteApp](/Diagrams/xrdp_w_mstsc_5.jpg)  
  
It’s pretty easy to setup in Azure – happy to walk you through it if you like.
You may have to grant users Local Admin rights on the VM where you publish MSTSC to the Linux box (I can help with that!).  

### X-Windows Access (likely the preferred method if you want a GUI)
You can do something similar with MobaXTerm or X2Go (and not mess around with XRDP!).  
**These may actually be the PREFFERED method so that the xRDP package is not required in the Linux VMs.**  
I do like X2Go published via RemoteApp – super simple user interface:  
![Xrdp RemoteApp](/Diagrams/x-windows_1.jpg)  
  
![Xrdp RemoteApp](/Diagrams/x-windows_2.jpg)  
  
…and then I’m into my full Linux Desktop (in this case, a Linux Data Science VM in Azure):  
![Xrdp RemoteApp](/Diagrams/x-windows_3.jpg)  
  
### Notes:
***Example:** Setting Ubuntu icon in Remote App config:  
![Xrdp RemoteApp](/Diagrams/ubuntu_remote_app_icon.png)  

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)