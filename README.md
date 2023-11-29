# Create an AppImage for the Proxmox Backup Client

The `proxmox-backup-client` is [only available for Debian
users](https://bugzilla.proxmox.com/show_bug.cgi?id=4788). Although it is
possible to install it into some Ubuntu releases and other derivatives of
Debian as well, it sometimes require some adjustments. And for some releases,
it is completely impossible to install due to dependency restrictions.

I was in need of the client for systems running Ubuntu 18.04 (Bionic).
Furthermore, the client should support namespaces, ruling out the
Buster-related release(s). Thus I started fiddling around with AppImage files.
While the one created with
[`pkg2appimage`](https://github.com/AppImageCommunity/pkg2appimage) did not
work due to relying on the libc provided by the host system, and that version
not matching the requirements of the packaged binaries,
[`appimage-builder`](https://github.com/AppImageCrafters/appimage-builder)
promises to package the glibc as well. I tried it and it seems to work at least
with the Bullseye version (2.x). The AppImage created with the Bookworm version
(3.x), unfortunately, fails with a [segmentation
fault](AppImageCrafters/appimage-builder#335).

To build the AppImage file, get the [`appimage-builder`
binary](https://github.com/AppImageCrafters/appimage-builder/releases/download/v1.1.0/appimage-builder-1.1.0-x86_64.AppImage)
(an AppImage itself). Then build it via:

```
./appimage-builder-1.1.0-x86_64.AppImage --recipe proxmox-backup-client.bullseye.yml --skip-tests
```

## USAGE

Download the appimage file, put it into `/usr/local/sbin/`, and make it
executable. Then use it as you would use the binaries provided via the Debian
package:

```
wget -O /usr/local/sbin/proxmox-backup-client https://github.com/dleidert/proxmox-backup-client.appimage/releases/download/Continuous/proxmox-backup-client-2.4.3-x86_64.AppImage
chmod +x /usr/local/sbin/proxmox-backup-client
proxmox-backup-client version
```

## LICENSE

The files are released into the public domain. Please note that the image
(`pkg2appimage` requires an image) has been taken from the Proxmox website in
good faith and is not subject to the license terms mentioned here.
