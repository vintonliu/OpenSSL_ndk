# OpenSSL_ndk
OpenSSl on the Android platform

Android NDK openssl build script for original repository(https://www.openssl.org/)

modified version of setenv-android.sh and build script support all architectures in the android NDK

see details : http://wiki.openssl.org/index.php/Android

Example:
OS: Ubuntu 16.04

NDK: [android-ndk-r13b](https://dl.google.com/android/repository/android-ndk-r13b-linux-x86_64.zip)(Do not use latest version)

OpenSSL: [openssl-1.0.2o](https://www.openssl.org/source/openssl-1.0.2o.tar.gz)

##### How to compile?
###### 1. Download NDK and set environment
Download
```
wget https://dl.google.com/android/repository/android-ndk-r13b-linux-x86_64.zip
```

Set environment, edit /etc/bash.bashrc, add the variable below at the file end
```
export ANDROID_NDK_ROOT=/home/android-ndk-r13b
export PATH=$PATH:$ANDROID_NDK_ROOT
```
Save and execute command below:
```
source /etc/bash.bashrc
```

###### 2. Clone and compile OpenSSL
Clone the code
```
git clone https://github.com/vintonliu/OpenSSL_ndk.git
```

Compile, execute the script
```
./build-all-arch.sh
```

Finally, you will get static and shared library at the prebuilt directory

 **_Note:_**
 Must specific the minSdkVersion equal to 21 or later in your build.gradle, else linked error would got like below:
 ```
 ui_openssl.c:function read_string_inner: error: undefined reference to 'signal'
 ```
 See https://github.com/openssl/openssl/issues/988 and https://www.jianshu.com/p/165f30813814