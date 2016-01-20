Odroid-C1 Gentoo Overlay
========================

This overlay includes ebuilds for the following packages:

* `app-misc/lcdproc`: lcdproc + Odroid-C1 patch
* `app-misc/odroidc1-remote`: Odroid C1 remote control setup (https://github.com/mdrjr/c1_irremote)
* `dev-embedded/u-boot-tools-odroidc1`: Odroid C1 U-Boot (https://github.com/hardkernel/u-boot)
* `dev-libs/wiringPi`: Fork of the wiringPi library with Odroid-C1 support
* `media-libs/aml-odroidc1`: Odroid C1 Amlogic Libraries (https://github.com/mdrjr/c1_aml_libs)
* `sys-kernel/odroidc1-sources`: Linux source for Odroid devices (https://github.com/hardkernel/linux)
* `x11-drivers/xf86-video-odroidc1`: Xorg DDX driver for Odroid-C1 (https://github.com/mdrjr/c1_mali_ddx)
* `x11-libs/odroidc1-mali`: Closed source drivers for Mali (https://github.com/mdrjr/c1_mali_libs)

Usage with Portage
------------------

```
mkdir /usr/local/portage
git clone git://github.com/tbe/odroidc1-overlay.git /usr/local/portage
echo 'PORTDIR_OVERLAY="${PORTDIR_OVERLAY} /usr/local/portage/"' >> /etc/portage/make.conf
```

Usage with Layman
-----------------
```
emerge -av layman dev-vcs/git
pico /etc/layman/layman.cfg
|   overlays  :
|       https://api.gentoo.org/overlays/repositories.xml
| +     https://github.com/tbe/odroidc1-overlay/raw/master/repositories.xml
layman -S
layman -a odroidc1
```

Usage with Paludis
------------------

```
cat > /etc/paludis/repositories/odroidc1.conf <<__EOF__
format = e
location = /var/db/paludis/repositories/odroid
sync = git://github.com/tbe/odroidc1-overlay.git
#master_repository = gentoo
names_cache = \${location}/.cache/names
write_cache = /var/cache/paludis/metadata
__EOF__
```
