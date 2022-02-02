
___________________________________________________________________________________

# CoreBook  X Gen8 Model JCorB   OpenCore

___________________________________________________________________________________

> ### ***I do not take any responsibility if you damage your devices.***
> ### ***The use of this material is not recommended, the procedure to be followed would be that reported in the Dortania guide with your files.***

___________________________________________________________________________________

### February 2022
> **Device is now 99% working!**

**Working:**
- Wifi and BT Intel
- Brightness Level from preferencies and menu bar
- HD Audio 
- I2C Trackpad with Gesture
- Automatic Keyboard backlight 
- Sleep / Wake with Lid detection
- Battery Status (No Service Recommended Notification) & AC Adapter detection

Not working:
- Brightness keys: 
  - No idea in how i can fix. Someone has an hint? Standard patching method are not working
  - If you long press f6 and f7 they will work laggy
- Ambient Light Sensor Device
  - Even if we found the Device in DSDT table, on my unit doesn't work in vanilla Windows 11 setup. Maybe sensor isn't installed in this model. [Need confirm]

Issue:
- Airdrop: 
  - Hope this will be added in AppleIntelWireless Road Map.   Actually not an issue for me..
- Battery Status:
  - Percentage report is missaligned
    - Nothing critical it takes a little more to reach full capability after the system report it as 100% (WIP)
    - Just check it with the led you have beside the plug.

___________________________________________________________________________________

# Guide

- ## BIOS Settings
  - ### Boot your Laptop and press ESC until you enter in BIOS settings.
  - ## Advanced:
    - Intel RC ACPI Settings:
      - Low Power S0 Idle Capability  **[ENABLED]**
      - PCI Delay Optimization        **[ENABLED]**
    - Power and Performance:
      - CPU Power Management and Control:
        - CPU Lock Configuration (_BOTTOM_)
          - CFG Lock **[DISABLED]**
    - Platform Thermal Configuration:
      - Active Trip Point 1           **[63]** 
      - > This only if for you the fan turns on and off every few seconds in certain cases
  - ## Chipset:
    - Graphics Configuration:
      - DVMT Pre-Allocated            **[64M]**
    - HD Audio Configuration:
      - HD Audio Advanced Configuration:
        - BT Intel HFP                **[ENABLED]**
        - BT Intel A2DP               **[ENABLED]**
  - ## Boot
      - Fast Boot                       **[DISABLED]**
___________________________________________________________________________________

# First Boot

- When booting for first time disable Force touch from Settings.<br/>
- When booting for first time go to Preferences > Keyboard > Modifier Keys and switch Command and Option values.<br/>
- Before any iService Activation open the config.plist with OpenCore configurator and in Platform Info tab select MacBookPro14,2 from list in DataHUB and SMBIOS and check for a valid (invalid for apple) serial.<br/>

> The serial number provided is random generated.



# For VoodooI2CHID:
- When downloading a new vesione just do: <br/>
1. 'Right Mouse Click on Kext -> Show Package Contents -> Contents -> info.plist'

2. Open it with xCode and change IOClass and Name like the image provided.<br/>
![VoodooI2CHID](https://user-images.githubusercontent.com/51327886/114537073-0f20ef00-9c52-11eb-9644-af826e872b7e.png)

# Credit
> ### [Acidanthera](https://github.com/acidanthera) for OpenCore, and all the public kexts. [License](https://github.com/acidanthera/OpenCorePkg/blob/master/LICENSE.txt)
> ### [OpenIntelWireless](https://github.com/OpenIntelWireless) for Intel Wifi and Bluetooth support. [License](https://github.com/OpenIntelWireless/itlwm/blob/master/LICENSE)
> ### Rehabman for ACPIPoller and a way to let me fix LID and AC detection.
> ### [weachy] for config.plist and kexts as starting point
> ### [rboldini](https://github.com/rboldini) for EC mapping, SSDT-BATT and SSDT-LID-AC coding. And his pacience and time.
> And me [terminet85](https://github.com/terminet85) for patching to support Model JCoreB (EC mapping, Battery Fix with A/C support) 
