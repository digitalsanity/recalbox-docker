# recalbox-docker

Launch and play recalbox/kodi (rockpro64/rock64 and Debian/Ubuntu host currently) via docker from your desktop.  Xorg will close but your services will continue.  Shutdown computer from Kodi to return to Recalbox.  Shutdown computer from Recalbox to return to Xorg.  Your settings are stored in $HOME/recalbox-share/

- This pulls the latest release from https://github.com/mrfixit2001/recalbox_*/releases and builds a docker container from the rootfs, allowing you to launch recalbox (and kodi) from most any debian/ubuntu host -- as long as the kernel rockchip version matches.  (4.4.171 tested, with arm64 kernel and armhf userspace)

# Steps

1. cd to this directory.
2. ./install.sh (not with sudo; if a RECALBOX folder pops up during install, close/ignore it; takes 15-20 minutes to complete)
3. Launch Recalbox from desktop application launcher (Media/Games/Video)

Run ./install.sh again at any time to update recalbox to the latest version.  Your settings/files/add-ons will be retained in $HOME/recalbox-share/

# Debugging steps

1. cd to this directory.
2. ./build-prepare.sh - Install Docker and dependencies.
3. ./build-rootfs.sh - Grab and build rootfs.  There will be some rsync errors/warnings - it's OK.
4. Optional: Review docker/rootfs and build-docker-from-rootfs.sh for files that will be removed.  Review docker/startup.sh for how the image is booted.
5. ./build-docker-from-rootfs.sh - Build docker from docker/rootfs.
6. Launch Recalbox or /usr/local/bin/recalbox-boot-stopx.sh from desktop, or close your desktop and launch /usr/local/bin/recalbox-boot.sh from tty1.

# Working/tested

- ROCKPro64 (RK3399)
  - https://github.com/ayufan-rock64/linux-build/releases 0.8.0rc5 or newer, mate armhf/bionic LXDE arm64 releases tested.  Must be on -1163 kernel or newer.
  - https://github.com/mrfixit2001/debian_desktop/releases - Second Release or newer.

# Should work

- ROCK64 (RK3328)
  - https://github.com/ayufan-rock64/linux-build/releases 0.8.0rc5 or newer, mate armhf/bionic LXDE arm64 releases.  Must be on -1163 kernel or newer.

# Other notes

- If you lose audio in Kodi, try different shutdown/reboot/quit options.  I think there may be an issue with multiple kodilauncher.sh running simultaneously.

Regards,
- Jason Fisher
- jason dot fisher at gmail dot com
