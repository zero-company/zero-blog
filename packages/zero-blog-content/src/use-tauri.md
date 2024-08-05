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

```
pnpm --filter @zero-company/zero-app tauri android init
```

https://v2.tauri.app/start/prerequisites/#android
https://v2.tauri.app/distribute/apk-sign/

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

Update the following
[project]/src-tauri/gen/android/keystore.properties
[project]/src-tauri/gen/android/app/build.gradle.kts, namespace, defaultConfig.applicationId
tauri.conf.json, identifier

# check if identified package name is available on google play

https://market.android.com/details?id=com.rovio.angrybirds

# privacy policy and terms of service template

https://github.com/ankane/awesome-legal

# file upload

https://uploadthing.com/

# googe play assets

- Create figma and storybook images
  - banner feature graphic, Your feature graphic must be a PNG or JPEG, up to 15 MB, and 1024 px by 500 px
  - phone screenshots, Upload 2-8 phone screenshots. Screenshots must be PNG or JPEG, up to 8 MB each, 16:9 or 9:16 aspect ratio, with each side between 320 px and 3,840 px, To be eligible for promotion, include at least 4 screenshots at a minimum of 1080 px on each side.
  - 7-inch tablet screenshots, Upload up to eight 7-inch tablet screenshots. Screenshots must be PNG or JPEG, up to 8 MB each, 16:9 or 9:16 aspect ratio, with each side between 320 px and 3,840 px
  - 10-inch tablet screenshots, Upload up to eight 10-inch tablet screenshots. Screenshots must be PNG or JPEG, up to 8 MB each, 16:9 or 9:16 aspect ratio, with each side between 1,080 px and 7,680 px

# vite vs next

https://www.reddit.com/r/reactjs/comments/14uyoab/choosing_between_nextjs_csrssr_and_vite/
