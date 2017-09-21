# 7. Wix Simple Complete Setup With UI Image Banners

This wix toolset project contain Welcome page image, Banner logo backbone, launch application after finished installing, Desktop Shorcut, Start Menu Shortcut and it install "Sample Application". Motive of the setup to provide basic knowledge of Wix Toolset Setup to beginners or newbie. Note: Installation is "perMachine", if you want to do "perUser" installation then see our other project named "5. Wix Simple Setup Per Machine Installer".

# Features!
  - Product.wxs with useful comments.
  - Install "Sample Application.exe"
  - UnInstall "Sample Application" from control panel.
  - Desktop Shortcut, Start Menu Shortcut, Application Icon.
  - Welcome ui with logo, top banner logo, option to select installation folder and launch installed application after installation.
  - Application Icon in control panel.
  - Check if .Net Framework 4.5.2 version is installed or not. If not show message and exit

Philosophy
>“Nothing is yours. It is to use. It is to share. If you will not share it, you >cannot use it.” 
> -Ursula K. Le Guin, The Dispossessed

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
  <PropertyRef Id="WIX_IS_NETFRAMEWORK_452_OR_LATER_INSTALLED" />
    <Condition Message="This application requires .NET Framework 4.5.2 Please install the .NET Framework then run this installer again.">
      <![CDATA[Installed OR WIX_IS_NETFRAMEWORK_452_OR_LATER_INSTALLED]]>
 </Condition>
```
Check if .Net Framework 4.5.2 version is installed or not. If not show message and exit.

```sh
<UI>
  <Publish Dialog="ExitDialog" Control="Finish" Event="DoAction" Value="LaunchApplication">WIXUI_EXITDIALOGOPTIONALCHECKBOX = 1 and NOT Installed</Publish>
</UI>
    <Property Id="WIXUI_EXITDIALOGOPTIONALCHECKBOXTEXT" Value="Launch $(var.Name)" />

    <!--Include the custom action for running application on exit-->
    <Property Id="WixShellExecTarget" Value="[#Sample_Application.exe]" />
    <Property Id="WIXUI_EXITDIALOGOPTIONALCHECKBOX" Value="1" />
    <CustomAction Id="LaunchApplication" BinaryKey="WixCA" DllEntry="WixShellExec" Impersonate="yes" />
```
Add CheckBox UI to your installer for running application on exit.

```sh
<Property Id="WIXUI_INSTALLDIR" Value="INSTALLFOLDER" />
    <UIRef Id="WixUI_InstallDir" />
    <!--EndUser License aggrement-->
    <WixVariable Id="WixUILicenseRtf" Overridable="yes" Value="Resources\eula.rtf" />
    <!--Top Banner UI Logo-->
    <WixVariable Id="WixUIBannerBmp" Overridable="yes" Value="Resources\TopBanner.jpg" />
    <!--Verticle Banner UI Logo-->
    <WixVariable Id="WixUIDialogBmp" Overridable="yes" Value="Resources\BackgroundLogo.jpg" />
```
Custom UI for installer with images and eula.

### Todos

 - Improve Documentation

### Want to contribute?

Great!! I will be happy to accept Git pull request!! 
I do this in my free time so please allow at least 2-4 days for me to respond to your comments or issues.

License
----
GNU General Public License v3.0
See Licese File for full text.