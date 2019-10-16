# OSX-KVM
<img src="https://img.shields.io/badge/stability-stable-green.svg?color=%23307ABE&style=flat-square"> <img src="https://img.shields.io/github/languages/code-size/benjaminstout/osx-kvm.svg?color=%23307ABE&style=flat-square"> <img src="https://img.shields.io/github/license/benjaminstout/osx-kvm.svg?color=%23307ABE&style=flat-square"> <img src="https://img.shields.io/github/downloads/benjaminstout/osx-kvm/total.svg?style=flat-square">

Software-based KVM Switcher for OSX. Simulates the double scroll lock LED toggle necessary to switch most KVMs.

Huge shoutout to [damieng](https://github.com/damieng) for his work on [setledsmac](https://github.com/damieng/setledsmac).

Tested and verified working through OSX 10.15 Catalina. If you'd like to test on other versions, let me know if it does or doesn't work for you!
## Usage:
Download and extract, open terminal, `cd` to the extracted folder, and execute `./kvmswitch`. Set up a [keyboard shortcut](#keyboard-shortcut) for hotkey support.
## Keyboard shortcut:
1. Move the `kvmswitch` file to `/Users/<your username>/bin/`
2. Double-click the included `Switch KVM.workflow` file
3. Click "Install" when prompted by the Quick Action Installer
4. This should automatically open service shortcuts, but if not, head to System Preferences > Keyboard > Shortcuts, and click "Services" in the left panel
5. Next to "Switch KVM" in the right panel, click on where it says "none", then click "Add Shortcut"
6. Press any key or key-combo to assign to the KVM switch
7. Profit!  
![](https://i.imgur.com/wfW5yLB.png)  
*__Note:__ If you would like to change the path of your kvmswitch file to something other than `/Users/<your username>/bin/`, right-click the `Switch KVM.workflowflow` file and click Open With > Automator.app, change ~/bin/kvmswitch to your new path, then click File > Save (⌘S). Proceed from step 2 above as normal.*
## How it works:
Most KVM switches monitor the state of the connected keyboard's scroll lock LED to use as its signal-switching "hotkey" input. Unfortunately, MacOS will often remap the key (F14) on external keyboards to decrease the display brightness, and does not support the necessary scroll lock LED toggle – until now. By employing the functionality of damieng's [setledsmac](https://github.com/damieng/setledsmac), we can quickly toggle the state of this LED in order to emulate the necessary KVM-switching signal.

The `kvmswitch` script spawns a new file, `kvmleds` which it uses to control keyboard LEDs, then toggles the scroll lock key 3 times in rapid succession (2 times to trigger the  switch, then once more in case the first did not register).
