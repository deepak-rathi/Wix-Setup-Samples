# 1. Wix Simple Setup

Wix Simple Setup is a project with basic backbone to install "Sample Application". Motive of the setup to provide basic knowledge of Wix Toolset Setup to beginners or newbie.

# Features!
  - Product.wxs with useful comments.
  - Install "Sample Application.exe".
  - UnInstall "Sample Application.exe" from control panel.
  - No Desktop Shortcut, No Start Menu Shortcut, No Application Icon.
  - "Sample Application.exe" can be found in program files and folder inside "Sample Company Name" folder.

Philosophy
>There is no wealth like knowledge,
>and no poverty like ignorance.
>Buddha
>(c. 400/500 BC, founder of Buddhism)

>Share your knowledge.
>It’s a way
>to achieve immortality.
>Dalai Lama

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

Basic XML tags:
```sh
<?xml version="1.0" encoding="UTF-8"?>
```
```sh
<Wix xmlns="http://schemas.microsoft.com/wix/2006/wi" />
```
```sh
<Product Id="*" Name="Wix_Simple_Setup" Language="1033" Version="1.0.0.0" Manufacturer="Your Company Name" UpgradeCode="8a83ac1e-fd2e-4737-bd75-257f10e0d7a9" />
```
Notes: 
```Product Id = "*" ``` here "\*" will generate a new GUID for us.
```Language="1033" ``` is telling our program that we need a Setup in "English" language.
```Manufacturer``` is for your company name.
```UpgradeCode``` its ```important``` and it should be a unique value for your setup. Do not change it if you release a updated version/ new version of your setup. Changing it will install a new copy of software with same name and version.

```sh
<MajorUpgrade DowngradeErrorMessage="A newer version of [ProductName] is already installed." />
```
```[ProductName]``` will be replaced by itself with the value and this message will be dispalyed to user if a newer version of setup is already installed on user machine.

```sh
<Fragment> </Fragment>
```
```Fragment``` can be used to ease the organising wxs file and improve readability and maintainability. They are building block of creating an installer database in WiX. Fragment becomes an immutable, atomic unit which can either be completely included or excluded from a product. The contents of a Fragment element can be linked into a product by utilizing one of the many *Ref elements.

```sh
<Directory Id="TARGETDIR" Name="SourceDir">
	<Directory Id="ProgramFilesFolder">
		<Directory Id="INSTALLFOLDER" Name="Wix_Simple_Setup" />
	</Directory>
</Directory>
```
```Directory``` tag is used for creating folders and also installing folder with in another directory. IN above code its targeting the ```ProgramFilesFolder``` Where application will be installed.

```sh
<ComponentGroup Id="ProductComponents" Directory="INSTALLFOLDER" />
```
``` ComponentGroup``` Groups together multiple components ```<Component /> ```

### Todos

 - Improve Documentation

### Want to contribute?

Great!! I will be happy to accept Git pull request!! 
I do this in my free time so please allow at least 2-4 days for me to respond to your comments or issues.

License
----
GNU General Public License v3.0
See Licese File for full text.