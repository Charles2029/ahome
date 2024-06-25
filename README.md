# a lovely home

Please to inform me ,and i will give you a back

```
# GitHub for personal
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

# GitHub for work
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

Host *
   AddKeysToAgent yes
   IdentitiesOnly yes
   ```
   ## [Step 1: Generate SSH Keys](https://pratapsharma.io/github-miltiple-key)
   ```
ssh-keygen
ssh-keygen -C work@domain.com
   ```

   These commands create public/private key pairs located in the ~/.ssh directory:

~/.ssh/id_rsa
~/.ssh/id_rsa.pub
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub

**remember**
input the passphrase

`eval "$(ssh-agent -s)"`
**eval "$(ssh-agent -s)"**
The above command is used to start the SSH agent and set up the necessary environment variables.
The above command is used to start the SSH agent and set up the necessary environment variables.

## Step 2: Modify SSH Config File

open this file: **~/.ssh/config**

Add the following *configuration*:
```
# GitHub for personal
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

# GitHub for work
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

Host *
   AddKeysToAgent yes
   IdentitiesOnly yes

```

# Step 3: Add Keys to macOS Keychain
Run the following commands to add keys to the Keychain:
```
eval "$(ssh-agent -s)"
ssh-add -D # This will delete all identities previously added
ssh-add --apple-use-keychain ~/.ssh/id_rsa
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```
ssh-add -D # This will **delete all**

Verify the added keys with:
`ssh-add -l`

## Step 4: [Add Public Keys to GitHub Accounts](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
Add the public keys to your GitHub accounts following GitHub's documentation.

`pbcopy < ~/.ssh/id_rsa.pub`

## Step 5: Test the Connection
```
ssh -T git@github.com
ssh -T git@github.com-work
```

## tep 7: Test it Out(not the important)
Create a repository on GitHub, clone it, and configure user email and name for the local repository:

For work account:
```
git config --local user.email "work@domain.com"
git config --local user.name "work"
```



