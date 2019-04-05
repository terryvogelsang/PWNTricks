# Mobile App Security



## ADB Commands

### List connected devices

`adb devices`

### Find package for app

`adb shell pm list packages | grep <your_app>`

### Find path for APK file

`adb shell pm path <your_package>`

### Extract file from device

`adb pull <path_to_file> <path_to_desired_destination>`

### Upload file to device
`adb push <path_to_file> <path_to_desired_destination>`

### Get info on application process

`adb shell ps | grep <your_app>`

### Check log for app

`adb logcat --pid=<pid_of_app>`

### Install APK on device

`adb install <path_to_file>.apk`

## Decompile APK into Java

`jadx app.apk -d <path_to_desired_destination>`

## Patch APK

### Decompile APK into Smali

`apktool d app.apk -o app.topatch`

### Recompile APK

`apktool d app.topatch -o app.patched.apk`

### Sign APK

`jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore ./Documents/tools/dummydata/patch.keystore  app.patched.apk patch`

### Align APK

`~/Library/Android/sdk/build-tools/28.0.3/zipalign -v 4 app.patched.apk app.patched.ready.apk`