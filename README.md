# blocklistmaker
Script to create blocklist of compromised private keys for the badkeys tool

# notes

If you merely want to use the [badkeys](https://github.com/badkeys/badkeys) tool you
don't need this. This is only supporting code to create the data badkeys downloads with
the *--update-bl*/*--update-bl-and-urls* parameters.

By default, badkeys utilizes private keys from the following repositories for its
blocklist:

```
 https://github.com/badkeys/debianopenssl
 https://github.com/badkeys/keypairvuln
 https://github.com/SecurityFail/kompromat
 https://github.com/SecurityFail/malware
 https://github.com/badkeys/webkeys
 https://github.com/badkeys/gitkeys
 https://github.com/badkeys/fortikeys
 https://github.com/badkeys/pkgkeys
 https://github.com/badkeys/fwkeys
 https://github.com/badkeys/osimagekeys
```

*blocklistmaker* is a python script to create truncated hashes in suitable formats for
badkeys.

# speed / performance

Some of the key repos contain very large directories, depending on the filesystem
accessing those can be very slow. The XFS filesystem is a good choice for performance.

The script disables some RSA consistency checks in python cryptography with the internal
_rsa_skip_check_key symbol, this is only supported in relatively recent versions. Also
we monkeypatch the cryptography backend to not enable RSA blinding, which also takes
significant time.

# about

[badkeys](https://badkeys.info/) and the support tooling was written by [Hanno Böck](
https://hboeck.de).
