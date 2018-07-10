# SSH KEYS

### Setup default identity
 1. `ssh-keygen`
 2. Enter the file name in which to save the key or enter to set default location.
 3. When asked for the passphrase, type it or press enter to omit it.
 4. Verify that key was successfully created: `ls ~/.ssh`
 5. By default we will have an RSA 2048b key

### Add key to the ssh-agent (In case the key was generated using password and we don't want to type it every time)
 1. To start the agent, run the following: `` eval `ssh-agent` ``
 2. Then: `ssh-add ~/.ssh/<private_key_file>`

