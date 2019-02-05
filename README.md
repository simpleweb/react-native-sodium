# react-native-sodium

Precompiled binaries of [libsodium](https://libsodium.org) will be linked by default.
Optionally, you can choose to compile libsodium by yourself (run __npm&nbsp;run&nbsp;rebuild__ in package directory). Source code will be downloaded and verified before compilation.

### Source compilation
###### General prerequisites
* gpg (macports, homebrew)

###### MacOS prerequisites
* libtool (macports, homebrew)
* autoconf (macports, homebrew)
* automake (macports, homebrew)


###### Android prerequisites
* Android NDK
* CMake
* LLDB

### Install

```
yarn add simpleweb/react-native-sodium
react-native link react-native-sodium
```
