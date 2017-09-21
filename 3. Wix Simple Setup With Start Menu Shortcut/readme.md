# 3. Wix Simple Setup With Start Menu Shortcut

Wix Simple Setup is a project with basic backbone to install "Sample Application". Motive of the setup to provide basic knowledge of Wix Toolset Setup to beginners or newbie. And create a Wix Setup which create "Sample Application" shortcut in "Start Menu".

# Features!
  - Product.wxs with useful comments.
  - Install "Sample Application.exe"
  - UnInstall "Sample Application" from control panel.
  - Start Menu Shortcut, Application Icon but No Desktop Shortcut.
  - Application Icon in control panel.

Philosophy
>In today's environment, hoarding knowledge ultimately erodes your power. If you >know something very important, the way to get power is by actually sharing it.     >-Joseph Badaracco

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
<ComponentRef Id="ApplicationShortcut" />
```

Let wix know we have a ComponentRef named ```ApplicationShortcut```
```sh
<Directory Id="ProgramMenuFolder">
    <Directory Id="ApplicationProgramsFolder" Name="$(var.Name)" />
</Directory>
```
Let wix know we need to access ```ProgramMenuFolder``` and create directory with our application name ( ```$(var.Name)``` is variable having our Application name defined in the same file).

```sh
<Fragment>
    <DirectoryRef Id="ApplicationProgramsFolder">
      <!--Create application shortcut in Program Menu-->
      <Component Id="ApplicationShortcut" Guid="*">
        <Shortcut Id="ApplicationStartMenuShortcut" Name="$(var.Name)" Description="$(var.Description)" Icon="Logo.ico" Target="[#Sample_Application.exe]" WorkingDirectory="INSTALLFOLDER" />
        <!--Remove application shortcut from Program Menu on uninstall-->
        <RemoveFolder Id="ApplicationProgramsFolder" On="uninstall" />
        <!--Create application registry entry-->
        <RegistryValue Root="HKCU" Key="Software\Microsoft\$(var.Manufacturer)\$(var.Name)" Name="installed" Type="integer" Value="1" KeyPath="yes" />
      </Component>
    </DirectoryRef>
</Fragment>
```
Fragment with ```ApplicationShortcut``` component, ```ApplicationStartMenuShortcut``` shortcut with application logo, ```WorkingDirectory``` tell's were to look for executable file in installed computer file system and ```Target``` tell's to look for file id "Sample_Application.exe".

```RemoveFolder``` tag tell wix that this shortcut neet to be removed on ```uninstall```.

We also do a  registery entry using tag ```RegistryValue``` at ```Software\Microsoft\$(var.Manufacturer)\$(var.Name)``` registry path.

### Todos

 - Improve Documentation

### Want to contribute?

Great!! I will be happy to accept Git pull request!! 
I do this in my free time so please allow at least 2-4 days for me to respond to your comments or issues.

License
----
GNU General Public License v3.0
See Licese File for full text.