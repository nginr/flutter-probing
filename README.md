# flutter-probing
Figuring out flutter with bits and pieces of android build system gotchas.

## Installation
### Download and unzip the [flutter](https://docs.flutter.dev/get-started/install/linux/android#download-then-install-flutter) and android [commandline-tools](https://developer.android.com/studio#command-tools) in `~/opt`.

```bash
$ mkdir -p ~/opt && cd ~/opt
$ tar -xvf ~/opt/flutter_linux_XXXXX-stable.tar.xz
$ unzip ~/opt/commandlinetools-linux-XXXXXXXX_latest.zip
$ mkdir -p ~/opt/android/cmdline-tools/latest
$ mv ~/opt/cmdline-tools/* ~/opt/android/cmdline-tools/latest/
```

### Update `PATH` variable (`~/.bashrc` or `~/.bash_profile`)
```bash
export PATH="$PATH:$HOME/opt/flutter/bin"

export ANDROID_HOME="$HOME/opt/android"
export ANDROID_EMULATOR_HOME="$XDG_CONFIG_HOME/.android"
export ANDROID_AVD_HOME="$ANDROID_EMULATOR_HOME/avd"
export PATH="$PATH:$ANDROID_HOME/cmdline-tools/latest/bin"
export PATH="$PATH:$ANDROID_HOME/platform-tools"
export PATH="$PATH:$ANDROID_HOME/emulator"
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
```bash
$ sdkmanager --install "cmdline-tools;latest"
$ sdkmanager "platform-tools" "platforms;android-26" "build-tools;26.0.0" "system-images;android-26;google_apis;x86"
$ sdkmanager --list_installed
```

### Create AVD and configure Emulator

```bash
$ sdkmanager "emulator"
$ avdmanager list device
$ avdmanager create avd -n <AVD_NAME> -k "system-images;android-26;google_apis;x86" \
     --device "Nexus 5" --sdcard 512M --tag "default" --abi "google_apis/x86"
$ emulator -avd <AVD_NAME>
```

 Or attach physical device (Make sure the host system JAVA is compatible with flutter projects android gradle)

### Resources
- [Android SDK - Command line tools Installation (Detailed)](https://www.youtube.com/watch?v=wvi03sOBKWQ)
- [android emulator](https://www.youtube.com/playlist?list=PLTyVJ9m1QDNcgm8l2xovDSm9YrT6y5wzx)
- [Flutter Course for Beginners – 37-hour Cross Platform App Development Tutorial](https://www.youtube.com/watch?v=VPvVD8t02U8)

## Misc
- [env-variables](https://developer.android.com/tools/variables)
- [adb-android-device-unauthorized](https://stackoverflow.com/questions/23081263/adb-android-device-unauthorized)
- [wireless-debugging](https://developer.android.com/studio/run/device#wireless)
- [emulator](https://developer.android.com/studio/run/emulator)
- [device](https://developer.android.com/studio/run/device)
