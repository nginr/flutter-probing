# flutter-probing
Figuring out flutter with bits and pieces of android build system gotchas.

## Installation
### Download and unzip the [flutter](https://docs.flutter.dev/get-started/install/linux/android#download-then-install-flutter) and android [commandline-tools](https://developer.android.com/studio#command-tools) in `~/opt`.

```bash
$ mkdir -p ~/opt && cd ~/opt
$ tar -xvf ~/opt/flutter_linux_XXXXX-stable.tar.xz
$ unzip ~/opt/commandlinetools-linux-XXXXXXXX_latest.zip
$ mkdir -p ~/opt/android/cmdline-tools/latest
```

### Update `PATH` variable (`~/.bashrc` or `~/.bash_profile`)
```bash
export FLUTTER_HOME="$PATH:$HOME/opt/flutter"
export ANDROID_HOME="$HOME/opt/android"
export ANDROID_EMULATOR_HOME="$XDG_CONFIG_HOME/.android"
export ANDROID_AVD_HOME="$ANDROID_EMULATOR_HOME/avd"

export PATH="$PATH:$FLUTTER_HOME/bin"
export PATH="$PATH:$ANDROID_HOME/tools"
export PATH="$PATH:$ANDROID_HOME/tools/bin"
export PATH="$PATH:$ANDROID_HOME/platform-tools"
```

### Check flutter version
```bash
$ flutter --version
Flutter 3.24.4 • channel stable • https://github.com/flutter/flutter.git
Framework • revision 603104015d (9 days ago) • 2024-10-24 08:01:25 -0700
Engine • revision db49896cf2
Tools • Dart 3.5.4 • DevTools 2.37.3
```

### Install Android SDK through [`sdkmanager`](https://developer.android.com/tools/sdkmanager)
The android [commandline-tools](https://developer.android.com/studio#command-tools)
in `~/opt/cmdline-tools/` may not be up-to-date. Download the `latest` by using `~/opt/cmdline-tools/bin/sdkmanager`
and then remove `~/opt/cmdline-tools/` directory.

```bash
$ ~/opt/cmdline-tools/bin/sdkmanager "cmdline-tools;latest"
$ sdkmanager "tools" "platform-tools" "platforms;android-26" \
      "build-tools;26.0.0" "emulator" "system-images;android-26;google_apis;x86"
$ sdkmanager --list_installed
```

### Create AVD and configure Emulator

```bash
$ avdmanager list device
$ avdmanager create avd -n <AVD_NAME> -k "system-images;android-26;google_apis;x86" \
     --device "Nexus 5" --sdcard 512M --tag "default" --abi "google_apis/x86"
$ emulator -avd <AVD_NAME>
```

 Or attach physical device (Make sure the host system JAVA is compatible with flutter projects android gradle)

### Resources
- [Android SDK - Command line tools Installation (Detailed)](https://www.youtube.com/watch?v=wvi03sOBKWQ)
- [android emulator](https://www.youtube.com/playlist?list=PLTyVJ9m1QDNcgm8l2xovDSm9YrT6y5wzx)
- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)
- [online documentation](https://docs.flutter.dev/)
- [Flutter Course for Beginners – 37-hour Cross Platform App Development Tutorial](https://www.youtube.com/watch?v=VPvVD8t02U8)
- [Flutter Course for Absolute Beginners | 2024 Latest](https://www.youtube.com/watch?v=DsTMhjaRQws)
- [Flutter Tutorial - Full Course - Project Based](https://www.youtube.com/watch?v=OO_-MbnXQzY)

## Misc
- [env-variables](https://developer.android.com/tools/variables)
- [adb-android-device-unauthorized](https://stackoverflow.com/questions/23081263/adb-android-device-unauthorized)
- [wireless-debugging](https://developer.android.com/studio/run/device#wireless)
- [emulator](https://developer.android.com/studio/run/emulator)
- [device](https://developer.android.com/studio/run/device)
