# ubuntu cheatsheet

## add sudo user
```
# add a new user
adduser <userName>

# add user to sudo
usermod -aG sudo <userName>
sudo visudo
<userName> ALL=(ALL) NOPASSWD:ALL
ssh <userName>@<server>
```
