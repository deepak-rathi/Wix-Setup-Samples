# 4. Wix Simple Setup With Desktop Shortcut

Wix Simple Setup is a project with basic backbone to install "Sample Application". Motive of the setup to provide basic knowledge of Wix Toolset Setup to beginners or newbie. And create a Wix Setup which create "Sample Application" desktop shortcut when isntalled.

# Features!
  - Product.wxs with useful comments.
  - Install "Sample Application.exe"
  - UnInstall "Sample Application" from control panel.
  - Desktop Shortcut, Application Icon but No Start Menu Shortcut.
  - Application Icon in control panel.

Philosophy
>If you have knowledge, let others light their candles in it.
>-Margaret Fuller

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
<ComponentGroupRef Id="ComponentGroupDesktopShortcut" />
```

Let wix know we have a ComponentRef named ```ComponentGroupDesktopShortcut```
```sh
<Directory Id="DesktopFolder" Name="DesktopFolder" />
```
Let wix know we need to access ```DesktopFolder``` and create shortcut with our application name ( ```$(var.Name)``` is variable having our Application name defined in the same file).

```sh
<Fragment>
    <!--Desktop Shortcut-->
    <ComponentGroup Id="ComponentGroupDesktopShortcut">
      <Component Id="ComponentDesktopShortcut" Guid="*" Directory="DesktopFolder" >
        <Shortcut Id="AppDesktopShortcut"
                  Name="$(var.Name)"
                  Description="$(var.Description)"
                  Directory="DesktopFolder"
                  Target="[#Sample_Application.exe]"
                  WorkingDirectory="INSTALLFOLDER"/>
        <!--Remove desktop shortcut on uninstall-->
        <RemoveFolder Id="DesktopFolder" On="uninstall"/>
        <RegistryValue Root="HKCU" Key="Software\$(var.Manufacturer)\$(var.Name)" Name="installed" Type="integer" Value="1" KeyPath="yes" />
      </Component>
    </ComponentGroup>
</Fragment>
```
Fragment with ```ComponentDesktopShortcut``` component, ```AppDesktopShortcut``` shortcut with application logo, ```WorkingDirectory``` tell's were to look for executable file in installed computer file system and ```Target``` tell's to look for file id "Sample_Application.exe".

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