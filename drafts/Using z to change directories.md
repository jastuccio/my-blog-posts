# Using z to change directories

Z is one of those 'where have you been all my life tools'

## Installation
### OSX
you can install it on OSX using `homebrew`

### Ubuntu
Thanks to [Josh Habdas](https://habd.as/installing-using-rupaz/) for the 'Nix install instructions

`$ cd /usr/local/bin`
`$ curl -O https://raw.githubusercontent.com/rupa/z/master/z.sh`
`$ chmod 775 z.sh`

`cd ~`

`nano .zshrc`

add to .zshrc

`# ensure z is available after each time the terminal emulator is opened`
`# https://github.com/rupa/z`
`. /usr/local/bin/z.sh`

