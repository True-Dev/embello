# AES-128 Encryption

[code]: any/aes128.fs ()
* Code: <a href="https://github.com/jeelabs/embello/tree/master/explore/1608-forth/flib/any/aes128.fs">any/aes128.fs</a>

This package implements AES-128 encryption and decryption of 16-byte blocks. It
supports encryption and decryption of arbitrary length (payload) buffers by
AES-CTR and calculation of a 'message authentication code'.

The decryption code is located in a separate `aes128inv.fs` file.

## API

[defs]: <> (aes)
```
: aes ( c-addr key -- ) \ aes128 encrypt block
```

[defs]: <> (aes-ctr aes-cmac)
```
: aes-ctr ( buf len key iv )              \ AES-CTR encrypt buffer. Encryption is in-situ.
: aes-cmac ( buf len key iv -- mic )      \ AES-CMAC hash key calculation
```

## Examples

Encrypt

    buf16 key aes

CTR

    buf-n len-n key initvector aes-ctr

CMAC

    buf-n len-n key initvector aes-cmac