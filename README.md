## Xanmod Kernel Binaries for Void Linux

Clone the `void-packages` official git repository and install the bootstrap packages:
```
$ git clone https://github.com/void-linux/void-packages.git
$ cd void-packages
$ ./xbps-src binary-bootstrap
$ cd ..
```

Modify `etc/conf` to build packages marked as 'restricted'
```
$ echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

Clone this repo in your home directory and then paste and replace the content of ```hostdir/``` into ```void-packages/hostdir/```

Download the binaries from the following links, and put them all in a single folder. Let me know if any of the links gets down.

https://anonfiles.com/udF0X6scz7/linux6_0_xanmod_6_0_3_1_x86_64_xbps

https://anonfiles.com/QdEfXbs1zd/linux6_0_xanmod_headers_6_0_3_1_x86_64_xbps

https://anonfiles.com/d0FdXfs8zf/linux6_2_xanmod_6_2_12_1_x86_64_xbps

https://anonfiles.com/P6E6X1sez9/linux6_2_xanmod_headers_6_2_12_1_x86_64_xbps

https://anonfiles.com/17L3X9s9z0/linux6_2_xanmod_dbg_6_2_12_1_x86_64_xbps


Copy every file except ```linux6.2-xanmod-dbg-6.2.12_1.x86_64.xbps``` to ```void-packages/hostdir/binpkgs```. Then, copy the remaining file to ```void-packages/hostdir/binpkgs/debug/```
```
sudo rsync -aP --exclude=linux6.2-xanmod-dbg-6.2.12_1.x86_64.xbps ~/single-folder-name/* ~/void-packages/hostdir/binpkgs && sudo cp ~/single-folder-name/linux6.2-xanmod-dbg-6.2.12_1.x86_64.xbps ~/void-packages/hostdir/binpkgs/debug
```

Now you can install the kernel by using the following command.
```
# sudo xbps-install --repository hostdir/binpkgs linuxX.X-xanmod linuxX.X-xanmod-headers
```

To finish the installation and make sure grub boot entries were added, use the ```xbps-reconfigure``` command.
```
$ sudo xbps-reconfigure -f linuxX.X-xanmod
```
