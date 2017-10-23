# GPG (OpenPGP) Commands

OpenPGP (Pretty Good Privacy) is a widely used email encryption standard. The OpenPGP protocol defines standard formats for encrypted messages, signatures, and certificates for exchanging public keys. It is defined by the OpenPGP Working Group of the Internet Engineering Task Force (IETF) as a Proposed Standard in RFC 4880. GnuPG is a complete and free implementation of the OpenPGP standard. Gpg4win is a Windows version of GnuPG. Learn more at:

http://openpgp.org/

https://www.ietf.org/rfc/rfc4880.txt

https://gnupg.org/

https://www.gpg4win.org/

## Examples of commands  

* __Generate a key pair__ `gpg --gen-key`

* __List all public keys__ `gpg --list-keys`

* __List all private keys__ `gpg --list-secret-keys`

* __Change a pass-phrase__ `gpg --change-passphrase support@quantclass.com`

* __Delete the public key__ `gpg --delete-key support@quantclass.com`

* __Delete the private key__ `gpg --delete-secret-key support@quantclass.com`

* __Export the private key__ `gpg -a --export-secret-keys support@quantclass.com | gpg -aco privatekey_gpg.asc`

* __Export the public key__ `gpg -a --export support@quantclass.com -ao publickey_gpg.asc`

* __Import a private key__ `gpg --allow-secret-key-import --import privatekey_gpg.asc`

* __Import a public key__
gpg --import publickey_gpg.asc support@quantclass.com

* __Encrypt a file__
gpg --encrypt -u support@quantclass.com file-to-secure.zip

* __Encrypt a file to a specific recipient__
gpg --encrypt -u support@quantclass.com -r <receiver-public-key> file-to-secure.zip

* __Decrypt an encrypted email attached__ `gpg --decrypt message.gpg > messaseg.eml`

* __Decrypt an encrypted zip file__ `gpg --decrypt file-to-secure.zip.gpg > file-to-secure.zip`

* __Generate a revocation certificate__ `gpg -ao publickey_gpg.rev --gen-revoke support@quantclass.com`

Note: It is considered best practice to generate a revocation certficate before sending to a public keyserver in case the certificate is compromised in the future (e.g. private key is made public).  

* __Send public key to a public keyserver__ `gpg --keyserver pgp.mit.edu --send-keys support@quantclass.com`

* __Get public key from a public keyserver__ `gpg --keyserver pgp.mit.edu --recv-key support@quantclass.com`
