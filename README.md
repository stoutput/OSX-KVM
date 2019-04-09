# OSX-KVM
Software-based KVM Switcher for OSX. Simulates the double scroll lock LED toggle necessary to switch most KVMs.

Huge shoutout to [damieng](https://github.com/damieng) for his work on [setledsmac](https://github.com/damieng/setledsmac).

Tested and verified working on MacOS Mojave. If you'd like to test on other versions, let me know if it does or doesn't work for you!
## Usage:
Simply download and run `./kvmswitch` from the terminal, or setup a [keyboard shortcut](#keyboard-shortcut).
## Keyboard shortcut:
1. Open Automator and click "Open an Existing Document..."
2. Browse to and choose the included `Switch KVM.workflow` file
3. Change `/path/to/kvmswitch` to the path of your downloaded `kvmswitch` file
4. Click on File > Save.
5. Open System Preferences > Keyboard > Shortcuts
6. Click on "Services" in the left panel, then find "Switch KVM" in the right panel
7. On the right of the "Switch KVM" line item, click on where it says "none", then click "Add Shortcut"
8. Press any key or key-combo to assign to the KVM switch
9. Profit!  
![](https://i.imgur.com/wfW5yLB.png)
## How it works:
Most KVM switches monitor the state of the connected keyboard's scroll lock LED to use as its signal-switching "hotkey" input. Unfortunately, MacOS will often remap the key (F14) on external keyboards to decrease the display brightness, and does not support the necessary scroll lock LED toggle – until now. By employing the functionality of damieng's [setledsmac](https://github.com/damieng/setledsmac), we can quickly toggle the state of this LED in order to emulate the necessary KVM-switching signal.
