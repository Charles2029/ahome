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
   