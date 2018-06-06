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
import Sodium from 'react-native-sodium';
import { Buffer } from 'buffer';

// Message to encrypt
const plaintext = 'Secret message';

// Generate keys
Sodium.crypto_box_keypair().then(keys => {
  console.log(`Public key: ${keys.pk}`);
  console.log(`Private key: ${keys.sk}`);

  // Base64 encode message
  const plaintext64 = Buffer.from(plaintext, 'utf8').toString('base64');

  // Encrypt
  Sodium.crypto_box_seal(plaintext64, keys.pk).then(encrypted => {
    console.log(`Encrypted: ${encrypted}`);

    // Decrypt
    Sodium.crypto_box_seal_open(encrypted, keys.pk, keys.sk).then(decrypted64 => {
      // Base64 decode
      const decrypted = Buffer.from(decrypted64, 'base64').toString('utf8');

      console.log(`Decrypted: ${decrypted}`);
      console.log(`Success? ${plaintext === decrypted}`);
    });
  });
});
```
