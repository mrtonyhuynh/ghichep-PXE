## File Preseed mẫu

Nguồn: https://www.hiroom2.com/2016/05/19/ubuntu-16-04-debian-8-run-pxe-boot-server-for-automated-install/

```
d-i debian-installer/locale string en_US
d-i debian-installer/language string en
d-i debian-installer/country string JP
d-i keyboard-configuration/xkb-keymap select jp106
d-i passwd/user-fullname string
d-i passwd/username string ubuntu
d-i passwd/root-password password ubuntu
d-i passwd/root-password-again password ubuntu
d-i passwd/user-password password ubuntu
d-i passwd/user-password-again password ubuntu
d-i user-setup/allow-password-weak boolean true
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i mirror/country string manual
d-i mirror/http/hostname string http://jp.archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
d-i clock-setup/utc boolean true
d-i clock-setup/ntp boolean true
d-i time/zone string Asia/Tokyo
d-i partman/confirm boolean true
d-i partman/choose_partition select finish
d-i partman/confirm_nooverwrite boolean true
d-i partman-auto/disk string /dev/[sv]da
d-i partman-auto/method string lvm
d-i partman-auto/choose_recipe select atomic
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-auto-lvm/guided_size string max
d-i partman-partitioning/confirm_write_new_label boolean true
d-i grub-installer/grub2_instead_of_grub_legacy boolean true
d-i grub-installer/only_debian boolean true
d-i grub-installer/bootdev string /dev/[sv]da
d-i pkgsel/update-policy select none
d-i pkgsel/include string unity ubuntu-desktop openssh-server
d-i finish-install/reboot_in_progress note
```

- Cài đặt Card mạng sử dụng DHCP

```
d-i netcfg/choose_interface select auto
```

- Cài đặt/Chia ổ cứng sử dụng LVM:

```
d-i partman-auto/disk string /dev/[sv]da
d-i partman-auto/method string lvm
d-i partman-auto/choose_recipe select atomic
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
```