# GPG / PGP Commands
=====================

Gpg4win is a Windows version of GnuPG.

https://gnupg.org/

https://www.gpg4win.org/

# Generate a key pair
gpg --gen-key 

# List all public keys 
gpg --list-keys 

# List all private keys 
gpg --list-secret-keys

# Change a pass-phrase 
gpg --change-passphrase support@quantclass.com

# Delete the public key 
gpg --delete-key support@quantclass.com

# Delete the private key 
gpg --delete-secret-key support@quantclass.com

Export the private key  
gpg -a --export-secret-keys support@quantclass.com | gpg -aco privatekey_gpg.asc

Export the public key  
gpg -a --export support@quantclass.com -ao publickey_gpg.asc

Import a private key
gpg --allow-secret-key-import --import privatekey_gpg.asc

Import a public key 
gpg --import publickey_gpg.asc support@quantclass.com

Encrypt a file 
gpg --encrypt -u support@quantclass.com file-to-secure.zip 

Encrypt a file to a specific person (for your eyes only) 
gpg --encrypt -u support@quantclass.com -r <receiver-public-key> file-to-secure.zip 

Decrypt a file 
gpg --decrypt message.gpg > messaseg.eml
gpg --decrypt file-to-secure.zip.gpg > file-to-secure.zip

Generate a revocation certificate before sending to a public keyserver
gpg -ao publickey_gpg.rev --gen-revoke support@quantclass.com

Send public key to a public keyserver
gpg --keyserver pgp.mit.edu --send-keys support@quantclass.com

Get public key from a public keyserver
gpg --keyserver pgp.mit.edu --recv-key support@quantclass.com
