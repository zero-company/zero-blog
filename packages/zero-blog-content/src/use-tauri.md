# generate icons

https://v2.tauri.app/reference/cli/#icon
https://github.com/tauri-apps/tauricon
https://www.pwabuilder.com/imageGenerator

# add tailwind and shadcn

https://dev.to/danimydev/tauri-react-shadcnui-1e8

```
npx shadcn-ui@latest add button
```

# deploy google play github actions ci

not officially supported, might go down any time, might be better to do manual release

https://www.valueof.io/blog/deploying-to-google-play-using-github-actions
https://github.com/r0adkll/sign-android-release
https://github.com/r0adkll/upload-google-play

# deploy

https://v2.tauri.app/start/prerequisites/#android

```
[System.Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\Program Files\Android\Android Studio\jbr", "User")

[System.Environment]::SetEnvironmentVariable("ANDROID_HOME", "E:\packages\android-sdk", "User")
$VERSION = Get-ChildItem -Name "E:\packages\android-sdk\ndk"
[System.Environment]::SetEnvironmentVariable("NDK_HOME", "E:\packages\android-sdk\ndk\$VERSION", "User")

$env:ANDROID_HOME

[System.Environment]::SetEnvironmentVariable("ANDROID_HOME", "$env:LocalAppData\Android\Sdk", "User")
$VERSION = Get-ChildItem -Name "$env:LocalAppData\Android\Sdk\ndk"
[System.Environment]::SetEnvironmentVariable("NDK_HOME", "$env:LocalAppData\Android\Sdk\ndk\$VERSION", "User")

rustup target add aarch64-linux-android armv7-linux-androideabi i686-linux-android x86_64-linux-android
```

# generate upload key, requires jdk
```
keytool -genkey -v -keystore $env:USERPROFILE\upload-keystore.jks -storetype JKS -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```
add to system environment variables, edit PATH
C:\Program Files\Android\Android Studio\jbr\bin
