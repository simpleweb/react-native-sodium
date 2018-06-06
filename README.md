# react-native-sodium

Sodium library is built from source (you should not trust a binary build when dealing with cryptography). Source code is downloaded and verified before compilation.

### General prerequisites

- gpg (macports, homebrew)

### macOS compilation prerequisites

- XCode
- libtool (macports, homebrew)
- autoconf (macports, homebrew)
- automake (macports, homebrew)

### Android prerequisites

- Android Studio
- SDK
- NDK
- CMake
- LLDB
- Environment variables

### Install

```
npm i simpleweb/react-native-sodium#sealed-boxes
react-native link react-native-sodium
npm i buffer
```

### How to use sealed boxes

```javascript
import Sodium from "react-native-sodium";
import { Buffer } from "buffer";

const sodiumBoxSealExample = async (plaintext: string) => {

  const keys = await Sodium.crypto_box_keypair();
  const { pk, sk } = keys;

  console.log(`Public key: ${pk}`);
  console.log(`Private key: ${sk}`);

  // Base64 encode message
  const encoded = Buffer.from(plaintext, "utf8").toString("base64");

  // Encrypt
  const encrypted = await Sodium.crypto_box_seal(encoded, pk);

  // Decrypt
  const decrypted = await Sodium.crypto_box_seal_open(encrypted, pk, sk);

  // Base64 decode
  const decoded = Buffer.from(decrypted, "base64").toString("utf8");

  console.log(`Decrypted and decoded: ${decoded}`);
  console.log(`Success? ${plaintext === decoded}`);
}

sodiumBoxSealExample("Encrypt me please");
```
