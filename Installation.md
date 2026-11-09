# Installation

[English](Installation.md) | [Bahasa Indonesia](Installation.id.md)

GRUB themes are not installed in exactly the same way on every distribution. Read the original theme's instructions first and check that it supports your GRUB version, boot mode, and display resolution.

## 1. Get the theme files

Open the theme's original project page from the catalog. Clone the repository or download its source archive from the project's own hosting service. If the theme is stored in a subdirectory, download the repository and use that theme folder.

Prefer manual installation when you are unsure what an install script changes. Review scripts before running them with administrator privileges.

## 2. Copy the theme

Create a directory for the theme and copy its files. The example below uses a Debian/Ubuntu-style path; your distribution may use a different GRUB directory.

```sh
sudo install -d /boot/grub/themes/my-theme
sudo cp -a ./my-theme/. /boot/grub/themes/my-theme/
```

The theme directory should contain its `theme.txt` file and the assets it references, such as images, fonts, and icons.

## 3. Configure GRUB

Edit `/etc/default/grub` with administrator privileges and set the path to the theme:

```sh
GRUB_THEME="/boot/grub/themes/my-theme/theme.txt"
```

Set `GRUB_GFXMODE` only when needed and choose a resolution supported by your display and GRUB. Keep a copy of your working configuration before changing it.

## 4. Regenerate the GRUB configuration

Use the command appropriate for your distribution:

- Debian and Ubuntu: `sudo update-grub`
- Fedora and openSUSE: `sudo grub2-mkconfig -o /boot/grub2/grub.cfg`
- Arch Linux and many other distributions: `sudo grub-mkconfig -o /boot/grub/grub.cfg`

Some distributions use a different output path. Follow your distribution's documentation rather than copying a command blindly.

## Notes

- Do not assume every theme supports every resolution, firmware mode, or GRUB version.
- Secure Boot policies may prevent unsigned fonts or other assets from loading. Follow your distribution's documented signing process; do not disable security features without understanding the consequences.
- Keep a recovery method and a known-good GRUB configuration available before changing bootloader settings.
- GRUB Customizer and third-party install scripts can modify more than the theme itself. Review their behavior before use.
