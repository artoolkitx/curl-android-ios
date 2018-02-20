curl-android-ios
================
The goal of this project is to provide a pre-compiled version of libcurl to be
used in Android and iOS.

It uses cURL from the upstream repository and it's updated frequently.

For Android, it also uses OpenSSL from its upstream repository.

If you want to build the library, scripts are provided for both platforms.
Test projects are also provided for both iOS and Android.

# Building
* Clone this repo `git clone git@github.com:gcesarmza/curl-android-ios.git`
* Clone submodules `git submodule init && git submodule update`
* Make sure you have installed autoconf, automake and libtool or install them with `apt-get` or `brew`
* When building on Mac OS make sure you have Xcode Command Line Developer Tools installed
```
xcode-select --install
```

## Building for Android:
* Download Android NDK
  * The Android NDK must support plattform `android-9` which is not available anymore inside the latest NDK versions (v16). Upgrading the build_Android.sh to `TARGET=android-27` or `TARGET=android-15` didn't work either because these versions lack the *include* directory. Final solution for me was to download NDK version [10e](https://developer.android.com/ndk/downloads/older_releases.html) which is able to build it. (There is another way to build it using the latest NDK and `TARGET=android-27` which is compiling the android toolchain as discribed here https://gist.github.com/Tydus/11109634 and copy the build includes from toolchain/sysroot/usr/include/ to platforms/android-27/arch-arm/usr/include/ but I'm not sure how future proof that is.)
```
cd curl-android-ios/curl-compile-scripts
export NDK_ROOT=PATH_WHERE_NDK_IS
./build_Android.sh
```

## Building for iOS
```
cd curl-android-ios/curl-compile-scripts
./build_iOS.sh
```
