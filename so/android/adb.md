---
description: >-
  Android Debug Bridge (adb) is a versatile command-line tool that lets you
  communicate with a device.
---

# adb

## Commands

### ADB Basics

```bash
adb devices (lists connected devices)
adb root (restarts adbd with root permissions)
adb start-server (starts the adb server)
adb kill-server (kills the adb server)
adb reboot (reboots the device)
adb devices -l (list of devices by product/model)
adb shell (starts the backround terminal)
exit (exits the background terminal)
adb help (list all commands)
adb -s <deviceName> <command> (redirect command to specific device)
adb –d <command> (directs command to only attached USB device)
adb –e <command> (directs command to only attached emulator)
```

### Package Installation

```bash
adb install <apk> (install app)  
adb install <path> (install app from phone path)  
adb install -r <path> (install app from phone path)
adb install-multiple <apk> config.* (install from xapk)
adb uninstall <name> (remove the app)
```

### Paths

```bash
/data/data/<package>/databases (app databases)
/data/data/<package>/shared_prefs/ (shared preferences)
/data/app (apk installed by user)
/system/app (pre-installed APK files)
/mmt/asec (encrypted apps) (App2SD)
/mmt/emmc (internal SD Card)
/mmt/adcard (external/internal SD Card)
/mmt/adcard/external_sd (external SD Card)

adb shell ls (list directory contents)
adb shell ls -s (print size of each file)
adb shell ls -R (list subdirectories recursively)
```

### File Operations

```bash
adb push <local> <remote> (copy file/dir to device)
adb pull <remote> <local> (copy file/dir from device)
run-as <package> cat <file> (access the private package files)
```

### Phone Info

```bash
adb get-statе (print device state)
adb get-serialno (get the serial number)
adb shell dumpsys iphonesybinfo (get the IMEI)
adb shell netstat (list TCP connectivity)
adb shell pwd (print current working directory)
adb shell dumpsys battery (battery status)
adb shell pm list features (list phone features)
adb shell service list (list all services)
adb shell dumpsys activity <package>/<activity> (activity info)
adb shell ps (print process status)
adb shell wm size (displays the current screen resolution)
adb shell getprop ro.product.cpu.abi (print CPU architecture)
dumpsys window windows | grep -E 'mCurrentFocus|mFocusedApp' (print current app's opened activity)
```

### Package Info

```bash
adb shell pm list packages (list package names)
adb shell pm list packages -r (list package name + path to apks)
adb shell pm list packages -3 (list third party package names)
adb shell pm list packages -s (list only system packages)
adb shell pm list packages -u (list package names + uninstalled)
adb shell dumpsys package packages (list info on all apps)
adb shell dump <name> (list info on one package)
adb shell path <package> (path to the apk file)
```

### Configure Settings Commands

```bash
adb shell dumpsys battery set level <n> (change the level from 0 to 100)
adb shell dumpsys battery set status<n> (change the level to unknown, charging, discharging, not charging or full)
adb shell dumpsys battery reset (reset the battery)
adb shell dumpsys battery set usb <n> (change the status of USB connection. ON or OFF)
adb shell wm size WxH (sets the resolution to WxH)
```

### Device Related Commands

```bash
adb reboot-recovery (reboot device into recovery mode)
adb reboot fastboot (reboot device into recovery mode)
adb shell screencap -p "/path/to/screenshot.png" (capture screenshot)
adb shell screenrecord "/path/to/record.mp4" (record device screen)
adb backup -apk -all -f backup.ab (backup settings and apps)
adb backup -apk -shared -all -f backup.ab (backup settings, apps and shared storage)
adb backup -apk -nosystem -all -f backup.ab (backup only non-system apps)
adb restore backup.ab (restore a previous backup)
adb shell am start|startservice|broadcast <INTENT>[<COMPONENT>]
-a <ACTION> e.g. android.intent.action.VIEW
-c <CATEGORY> e.g. android.intent.category.LAUNCHER (start activity intent)

adb shell am start com.example.app/.SecretActivity
adb shell am start -a android.intent.action.VIEW -d URL (open URL)
adb shell am start -t image/* -a android.intent.action.VIEW (opens gallery)
```

### Logs

```bash
adb logcat [options] [filter] (view device log. Ex: adb logcat com.android.app -b all -v color)
adb bugreport (print bug reports)
```

### Permissions

```bash
adb shell permissions groups (list permission groups definitions)
adb shell list permissions -g -r (list permissions details)
```

### Commonly used commands

#### Download APK from mobile device

<pre class="language-bash"><code class="lang-bash"><strong>adb shell pm list packages
</strong>adb shell pm path com.example.someapp
adb pull /data/app/com.example.someapp-2.apk path/to/desired/destination

# If the apk is divided in multiple parts

</code></pre>

## References

{% embed url="https://developer.android.com/studio/command-line/adb?hl=es-419" %}
