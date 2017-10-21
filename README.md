# GPG / PGP Commands


Gpg4win is a Windows version of GnuPG.

https://gnupg.org/

https://www.gpg4win.org/

* __Generate a key pair__
gpg --gen-key 

* __List all public keys__
gpg --list-keys 

* __List all private keys__
gpg --list-secret-keys

* __Change a pass-phrase__ 
gpg --change-passphrase support@quantclass.com

* __Delete the public key__ 
gpg --delete-key support@quantclass.com

* __Delete the private key__ 
gpg --delete-secret-key support@quantclass.com

* __Export the private key__  
gpg -a --export-secret-keys support@quantclass.com | gpg -aco privatekey_gpg.asc

* __Export the public key__ 
gpg -a --export support@quantclass.com -ao publickey_gpg.asc

* __Import a private key__
gpg --allow-secret-key-import --import privatekey_gpg.asc

* __Import a public key__ 
gpg --import publickey_gpg.asc support@quantclass.com

* __Encrypt a file__ 
gpg --encrypt -u support@quantclass.com file-to-secure.zip 

* __Encrypt a file to a specific recipient__ 
gpg --encrypt -u support@quantclass.com -r <receiver-public-key> file-to-secure.zip 

* __Decrypt a file__ 
gpg --decrypt message.gpg > messaseg.eml OR
gpg --decrypt file-to-secure.zip.gpg > file-to-secure.zip

* __Generate a revocation certificate (before sending to a public keyserver)__
gpg -ao publickey_gpg.rev --gen-revoke support@quantclass.com

* __Send public key to a public keyserver__
gpg --keyserver pgp.mit.edu --send-keys support@quantclass.com

* __Get public key from a public keyserver__
gpg --keyserver pgp.mit.edu --recv-key support@quantclass.com
