<img align="right" src="https://github.com/n00b69/woa-everything/blob/main/devices.png" width="350" alt="Windows 11 running on a cellphone">

# Running Windows on your cellphone

## Updating drivers

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [UEFI image](https://github.com/n00b69/woa-everything/releases/tag/UEFI)
  
- [Drivers](https://github.com/n00b69/woa-everything/releases/tag/Drivers)
  
- [Msc script](https://github.com/n00b69/woa-everything/releases/download/Files/msc.sh)
  
- TWRP or any other recovery

#### Boot to TWRP
> If COMPANY has replaced your recovery back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Running the msc script
> Put msc.sh in the platform-tools folder, then run:
```cmd
adb push msc.sh / && adb shell sh msc.sh
```

### Diskpart
```cmd
diskpart
```

#### List device volumes
> To print a list of all the connected volumes, run
```cmd
list volume
```

#### Select Windows volume
> Replace $ with the actual number of **WIN**
```cmd
select volume $
```

#### Assign letter to Windows
```cmd
assign letter x
```

#### Exit diskpart
```cmd
exit
```

### Installing Drivers
> Extract the drivers folder from the archive, then run the following command, replacing`<path\to\drivers>` with the actual path of the drivers folder
```cmd
dism /image:X:\ /add-driver /driver:<path\to\drivers> /recurse
```

### Unassign disk letter
> So that it doesn't stay there after disconnecting the device
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **WIN**
```diskpart
select volume $
```

#### Unassign the letter X
```diskpart
remove letter x
```

#### Exit diskpart
```diskpart
exit
```

##### Boot back into Windows
> Reboot your device to boot back into Windows. If this boots you to Android, reflash the UEFI image through fastboot or by using the WOA Helper app


## Finished!



















