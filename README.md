# sammy-nogood

Debloating Samsung Galaxy S20+ 5g (snapdragon, y2q, gm986u) as thin as possible without breaking it.

# why 

Basically I'm just annoyed at the difficulty in telling telemetry apart from malicious activity, so since I don't want to shell out the cash to get the bootloader unlocked, I'd like to automate the process of suppressing as much of the garbage as I can when I reset the thing.

# also

There are a bunch of packages that pop up from time to time that break things and force you to have to restart the process, I'd like to get a good running list of these things I can pull down with termux at first boot.

# termux

It's a great tool because you don't need a computer to connect your sketchy phone to via USB where it gets direct memory access and probably does something with it, or maintains tools poorly enough for the drivers to sideload plugx (that happened, ref: https://unit42.paloaltonetworks.com/plugx-uses-legitimate-samsung-application-for-dll-side-loading/).

# the process

If you want to mirror what I'm doing, and you have the same model, the flow is:

Get F-Droid
Download Termux
$ pkg update
$ pkg install android-tools git vim
Open Termux in pop-up view from the ||| button menu and a long press on the Termux icon.
Open Settings > Developer Options in the background > Enable Wireless Debugging > Click Wireless Debugging > Pair with code
In Termux in pop-up view over the settings screen >
$ adb pair <YOUR-IP>:<PORT-SEEN-IN-PAIRING-POP-UP> <PAIRING-CODE>
It should pair then, but usually you still need to run:
$ adb connect <PORT-SHOWN-IN-MENU> 
Bear in mind this is typicall a different port. Once you're connected, you pull a list from here or where ever and run it via:
$ bash script.sh && adb shell reboot
Probably read it before you run in into bash, y'know, just sayin'.

Donezo.
