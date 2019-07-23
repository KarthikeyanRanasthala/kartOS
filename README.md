# kartOS

A Custom Debian Based Linux Operating System.


## Details

Linux Kernel - 4.19.37-5

Base - Debian 10 Buster

Desktop Environment - KDE Plasma 5 (kde-plasma-desktop)

Included Applications - Brave Browser (brave-browser), Github Desktop (github-desktop), Python 3 (python3 python3-pip), VLC Media Player (vlc), VS Code (code)

Note: Brave Browser, Github Desktop & VS Code are not available in Debian's repository. So, they're installed using hooks during the chroot stage.


## How to Build kartOS

```
sudo apt-get install live-build
sudo lb config --config https://www.github.com/KarthikeyanRanasthala/kartOS.git
sudo lb build
```


## Stages of the build

The build process is divided into different stages with varoius customizations applied in sequence in each stage. 
The Bootstrap stage is the initial phase of populating the chroot directory with packages to make a barebones Debian system.
This is followed by the chroot stage in which the chroot directory is contructed by populating it with all the packages listed in the configuration along with any other hooks. Most customization of the content occurs in this stage.
The binary stage is the final stage in which a bootable image is built using the contents of chroot directory to contruct the root filesystem and including the installer on the target medium outside the filesystem.
Within each of these stages, there is a particular sequence in which commands are applied. These are arranged in such a way as to ensure customizations can be layered in a reasonable fashion.


## References

1. Live System Manual - https://live-team.pages.debian.net/live-manual/html/live-manual/about-manual.en.html
1. Live Build Manual - https://manpages.debian.org/buster/live-build/live-build.7.en.html