# arch-thinkpad-x200
Install instructions for my configuration of arch on my x200

make boot iso

cfdisk
  / 30G
  swap 4G
  /home rest
  
  mkfs.ext4 /dev/*** for boot home and root
  mkswap for /dev/*** swap
  swapon /dev/***
  
  mount /dev/(root) /mnt
  mkdir /mnt/boot /mnt/home
  mount /dev/(home) /mnt/home
  
  timedatecctl set-ntp true
  wifi-menu 
  
  pacstrap /mnt base linux linux-firmware
  
genfstab -U /mnt >> /mnt/etc/fstab
   
 ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
 
 hwclock --systohc

locale-gen

/etc/locale.conf
  LANG=en_US.UTF-8
  
/etc/hostname
  $(myhostname)
mkinitcpio -P

passwd
