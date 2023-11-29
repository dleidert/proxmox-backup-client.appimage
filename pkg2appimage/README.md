# Create an AppImage for the Proxmox Backup Client with pkg2appimage

For historical reasons. Download the [`pkg2appimage` AppImage
file](https://github.com/AppImageCommunity/pkg2appimage/releases/download/continuous/pkg2appimage--x86_64.AppImage)
and do:

```
./pkg2appimage--x86_64.AppImage proxmox-backup-client.bookworm.yml
```

The glibc-requirements must be fulfilled by the target system.

## LICENSE

The files are released into the public domain. Please note that the image
(`pkg2appimage` requires an image) has been taken from the Proxmox website in
good faith and is not subject to the license terms mentioned here.
