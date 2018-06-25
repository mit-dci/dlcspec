# Oracle Schnorr Signature

## Introduction

This document uses Schnorr Signature on an elliptic curve.

`G` is the base point of the elliptic curve.

Oracle public key and private key.  `V = vG`

Random keys. `R = rG`

Sign is `s`.

Message is `m`.

---

## Schnorr Signature

    sG = R - H(R,m)V
    s = r - H(R,m)v

---
## Hash function

    H(R,m) = sha256(R || m)

`R` is compress EC point.

Head is `0x02` or `0x03` and 33 bytes length.

So, concatenate message.

Example.

    R = 02989df59fc563bb46c3970e5efb6849aaa60f4a6a3222e53d5437d108d4d0c75a
    m = 00000001
    H(R,m) = sha256(02989df59fc563bb46c3970e5efb6849aaa60f4a6a3222e53d5437d108d4d0c75a00000001)
           = 3bb02106aa486097945c3ade0a817b92f8de51e63d2967f647f7433109c3c8f7

---
