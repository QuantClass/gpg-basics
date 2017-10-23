# GPG Class

Email privacy is an important step to ensure that your communication is safe from prying eyes.
These are the steps to generate and manage the key pair (public and private) for user _support@quantclass.com_. There are GUI versions of the key management tools, such as GPG Keychain on MacOS and Kleopatra for Linux and Windows. Kleopatra is a certificate manager and a universal crypto GUI that supports managing both X.509 and OpenPGP certificates. In this class we will use the command-line version of the tools, as this gives you more freedom.

First, download the tools from   

https://gnupg.org/

https://www.gpg4win.org/

to follow-up with us.

**You will learn faster if you do it yourself**.

The main commands are:

## 1. Generate a key pair

```$ gpg --gen-key
gpg (GnuPG/MacGPG2) 2.2.0; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Support Team at QuantClass.com
Email address: support@quantclass.com
You selected this USER-ID:
    "Support Team at QuantClass.com <support@quantclass.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 85E61D023FD9A9C7 marked as ultimately trusted
gpg: revocation certificate stored as '/Users/fcbarbi/.gnupg/openpgp-revocs.d/8D57558AC93D240BCA7E1AEE85E61D023FD9A9C7.rev'
public and secret key created and signed.

pub   rsa2048 2017-10-23 [SC] [expires: 2019-10-23]
      8D57558AC93D240BCA7E1AEE85E61D023FD9A9C7
uid                      Support Team at QuantClass.com <support@quantclass.com>
sub   rsa2048 2017-10-23 [E] [expires: 2019-10-23]
```

Note the string **8D57558AC93D240BCA7E1AEE85E61D023FD9A9C7** is know as the *fingertip* of the certificate.

## 2.List all public keys

```
$ gpg --list-keys
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
gpg: next trustdb check due at 2019-10-23
/Users/fcbarbi/.gnupg/pubring.gpg
---------------------------------
pub   dsa2048 2010-08-19 [SC] [expires: 2018-08-19]
      85E38F69046B44C1EC9FB07B76D78F0500D026C4
uid           [ unknown] GPGTools Team <team@gpgtools.org>
uid           [ unknown] GPGMail Project Team (Official OpenPGP Key) <gpgmail-devel@lists.gpgmail.org>
uid           [ unknown] GPGTools Project Team (Official OpenPGP Key) <gpgtools-org@lists.gpgtools.org>
uid           [ unknown] [jpeg image of size 5871]
sub   elg2048 2010-08-19 [E] [expires: 2018-08-19]
sub   rsa4096 2014-04-08 [S] [expires: 2024-01-02]

pub   rsa4096 2017-05-07 [SC] [expires: 2021-05-07]
      CEAF9328A48F49981A588058944670F4E183B4CF
uid           [ultimate] Fernando C Barbi <fcbarbi@gmail.com>
sub   rsa4096 2017-05-07 [E] [expires: 2021-05-07]

(other public keys omitted)

pub   rsa2048 2017-10-23 [SC] [expires: 2019-10-23]
      8D57558AC93D240BCA7E1AEE85E61D023FD9A9C7
uid           [ultimate] Support Team at QuantClass.com <support@quantclass.com>
sub   rsa2048 2017-10-23 [E] [expires: 2019-10-23]
```

Note that keys are kept in the file `/Users/fcbarbi/.gnupg/pubring.gpg`. All the public keys that you have installed are listed here, I just omitted them for clarity.

## 3.List all private keys

```$ gpg --list-secret-keys
/Users/fcbarbi/.gnupg/pubring.gpg
---------------------------------
sec   rsa4096 2017-05-07 [SC] [expires: 2021-05-07]
      CEAF9328A48F49981A588058944670F4E183B4CF
uid           [ultimate] Fernando C Barbi <fcbarbi@gmail.com>
ssb   rsa4096 2017-05-07 [E] [expires: 2021-05-07]

sec   rsa2048 2017-10-23 [SC] [expires: 2019-10-23]
      8D57558AC93D240BCA7E1AEE85E61D023FD9A9C7
uid           [ultimate] Support Team at QuantClass.com <support@quantclass.com>
ssb   rsa2048 2017-10-23 [E] [expires: 2019-10-23]
```

Note that only private keys are listed. As you NEVER SHARE YOUR PRIVATE KEY (we will see two exceptions to this rule) with anyone the only two keys listed are the ones that I have on my computer. In the case of a shared email address like `support@quantclass.com` there is one exception to the rule and you may share the PRIVATE KEY with other users in the support team that also must send encrypted messages. I will show later how to export this private key to share it internally. It is also a good idea to export it to safeguard it in a backup media.

## 4.Change a pass-phrase

```
$ gpg --change-passphrase support@quantclass.com
gpg (GnuPG/MacGPG2) 2.2.0; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

You first provide the current passphrase and then the new one, that you confirm by typing again.

## 5.Export the private key

## 6.Export the public key

## 7.Delete the public key

__Can I regenerate the public key from the private key?__

## 8.Delete the private key

## 9.Import a private key

## 10.Import a public key

## 11.Encrypt a file to any reader

## 12.Encrypt a file to a specific recipient

## 13.Decrypt an encrypted

You received an encrypted email but since your client don't now how to open it the message is attached. The first step is to save it as a `message.gpg`. As we decrypt it, a new file will be generated named `message.eml`. This is achived with the command:

```
$ gpg --decrypt message.gpg > messaseg.eml
```

To decrypt an encrypted zip file you can call
```
$ gpg --decrypt file-to-secure.zip.gpg > file-to-secure.zip
```
If the file is saved with an additional layer of security it may require a passphrase to be opened.

Note that the encrypted file has a `.gpg`extension to indicate how it was encrypted. We recommend you follow this convention to document your files.

## 14.Generate a revocation certificate

## 15.Send public key to a public keyserver

## 16.Get public key from a public keyserver
