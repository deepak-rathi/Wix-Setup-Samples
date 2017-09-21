# 5. Wix Simple Setup Per Machine Installer

Wix Simple Setup is a project with basic backbone to install "Sample Application". Motive of the setup to provide basic knowledge of Wix Toolset Setup to beginners or newbie. And create a Wix Setup which install "Sample Application" per machine.

# Features!
  - Product.wxs with useful comments.
  - Install "Sample Application.exe"
  - UnInstall "Sample Application" from control panel.
  - Desktop Shortcut, Start Menu Shortcut, Application Icon.
  - Application Icon in control panel.

Philosophy
>“It ain't no fun if the homies can't have none. ” 
> -Snoop Dogg

### Installing Wix Toolset

This project requires Wix Toolset Build Tools and Wix Toolset Visual Studio Extension. Feel free to select your own version as per your project need, but for simplicity we can downloaded for Visual Studio 2017 and Wix v3.11, from below links:

* [Wix Toolset Visual Studio Extension](https://marketplace.visualstudio.com/vsgallery/2eb3402e-ea6d-4dcd-8340-c88435e54ea9) - WiX Toolset Visual Studio 2017 Extension
* [Wix Toolset Build Tools](http://wixtoolset.org/releases/v3.11/stable) - Wix Toolset Build Tools v3.11

And of latest version please visit [Wix Toolset Website](http://wixtoolset.org/releases/)


### Documentation

Intial guide or manual to get started with Wix Toolset and some useful links from Wix Toolset website are as below.

| Topic | Links |
| ------ | ------ |
| Introduction | http://wixtoolset.org/documentation/manual/v3/main/ |
| How To Guides | http://wixtoolset.org/documentation/manual/v3/howtos/ |
| Complete Manual | http://wixtoolset.org/documentation/manual/v3/ |
| Tutorials | https://www.firegiant.com/wix/tutorial/ |

#### Let's get started

Code to look for is as below:
```sh
<Package InstallerVersion="200" Compressed="yes" InstallScope="perMachine" Manufacturer="$(var.Manufacturer)" />
```

```InstallScope``` tell wix that we want installation to be ```perMachine```


### Todos

 - Improve Documentation

### Want to contribute?

Great!! I will be happy to accept Git pull request!! 
I do this in my free time so please allow at least 2-4 days for me to respond to your comments or issues.

License
----
GNU General Public License v3.0
See Licese File for full text.