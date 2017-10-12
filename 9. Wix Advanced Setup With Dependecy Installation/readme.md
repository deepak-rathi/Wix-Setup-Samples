# 9. Wix Advanced Setup With Dependecy Installation
Wix Advanced Setup With Dependecy Installation is a Wix Bootstrapper project with basic backbone to install "Sample Application" along with .Net Framework 4.5.2 using offline isntaller. Motive of the setup to provide basic knowledge of Wix Toolset bootstrapper Setup to beginners or newbie.

# Features!
- Bootstrapper 
  - Install .net Framework 4.5.2 using offline installer and then install Simple Application using Main Setup msi
  - Bootstrapper setup with logo, EULA.
  - Bootstrapper with suppressed options UI and suppressed repair UI
- Main Setup
  - Product.wxs with useful comments.
  - Install "Sample Application.exe"
  - UnInstall "Sample Application" from control panel.
  - Desktop Shortcut, Start Menu Shortcut, Application Icon.
  - Welcome ui with logo, top banner logo, option to select installation folder and launch installed application after installation.
  - Application Icon in control panel.
  - Checks if .Net Framework 4.5.2 version is installed or not. If not show message and exit

Philosophy
>जितना कम आप अपना ह्रदय दूसरों के समक्ष खोलेंगे , उतनी अधिक आपके ह्रदय को पीड़ा होगी. || The less you open your heart to others, the more your heart suffers. – Deepak Chopra

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
| ------ | ------ |
| Bootstrapping | https://www.firegiant.com/wix/tutorial/net-and-net/bootstrapping/ |
| Bal Extension | http://wixtoolset.org/documentation/manual/v3/xsd/bal/wixstandardbootstrapperapplication.html |
| WiX Standard Bootstrapper Application | http://wixtoolset.org/documentation/manual/v3/bundle/wixstdba/ |
| Using Project References and Variables | http://wixtoolset.org/documentation/manual/v3/votive/votive_project_references.html |
| How To: Install the .NET Framework Using Burn | http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html |

#### Let's get started

Code to look for is as below:
```sh
<?define Logo = "Resources\logo.ico" ?>
```

Defined ```Logo``` variable with ```logo.ico``` image from Resources folder
```sh
<?define Eula = "Resources\eula.rtf" ?>
```
Defined ```EULA``` variable for EULA rtf document from Resources folder

```sh
<BootstrapperApplicationRef Id="WixStandardBootstrapperApplication.RtfLicense">
      <bal:WixStandardBootstrapperApplication LicenseFile="$(var.Eula)" LogoFile="$(var.Logo)" SuppressOptionsUI ="yes" SuppressRepair="yes"/>
</BootstrapperApplicationRef>
```

```LicenseUrl ``` is kept empty such that no license is displayed for bootstrapper setup.
```LogoFile ``` is logo for bootstrapper setup and not for the application.
```SuppressOptionUI ``` removes option button allowing user to select installation loaction from bootstrapper setup project.

```sh
<PackageGroupRef Id="NetFx452Redist" />
```
```NetFx452Web```Installs .Net Framework 4.5.2 using offline installer, for more option see Wix documentation at http://wixtoolset.org/documentation/manual/v3/customactions/wixnetfxextension.html

```sh
<PayloadGroup Id="NetFx452RedistPayload">
  <Payload Name="redist\NDP452-KB2901907-x86-x64-AllOS-ENU.exe" SourceFile="Resources\NDP452-KB2901907-x86-x64-AllOS-ENU.exe"/>
</PayloadGroup>
```
```Payload``` let us use already downloaded .Net Framework setup for creating offline installer

```Add Setup from previous project 7. Wix Simple Complete Setup With UI Image Banners. to reference```
```sh
<MsiPackage DisplayName="$(var.Name)" SourceFile="$(var.Wix Simple Complete Setup.TargetPath)" Compressed="yes" Vital="yes"/>
```
```Above code will install main setup created in previous project 7. Wix Simple Complete Setup With UI Image Banners.```

### Todos

 - Improve Documentation

### Want to contribute?

Great!! I will be happy to accept Git pull request!! 
I do this in my free time so please allow at least 2-4 days for me to respond to your comments or issues.

License
----
GNU General Public License v3.0
See Licese File for full text.