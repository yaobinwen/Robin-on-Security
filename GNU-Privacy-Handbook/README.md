# The (Unofficial) GNU Privacy Handbook

## About the Unofficial Handbook

The [_The GNU Privacy Handbook_](https://www.gnupg.org/gph/en/manual.html) uses `gpg` 0.9.4 and is out-dated.

## Key Pair, Fingerprint, and Key IDs

A key pair consists of a private key and the corresponding public key. A key pair uses its "fingerprint" to uniquely identify itself.

The "fingerprint" is the full ID of the key pair. Section "12.2. Key IDs and Fingerprints" in _RFC 4880: OpenPGP Message Format_ defines that:

> A V4 fingerprint is the 160-bit SHA-1 hash of the octet 0x99, followed by the two-octet packet length, followed by the entire Public-Key packet starting with the version field.

A key pair also has a "long key ID" and a "short key ID", but these two IDs are derived from the fingerprint by using the lower bytes of the fingerprint. For example:

```
fingerprint: 51C6B2E842538F3C05BE25FA9CF0B1DD45414C71
long ID:                             9CF0B1DD45414C71
short ID:                                    45414C71
```

The terms "public key" and "private key" give people the impression that these two keys can be treated separately. Therefore, one may naturally think that the public key and the private key would have their own IDs. In fact, they share the same key ID which is the fingerprint of the key pair: there is no "public key ID" or "private key ID". Therefore, it is better to always see the key pair as an whole entity.

