# ArchLinux-Installation-Guide





ArchLinux Basic Installation ITALIAN



Guida Installazione ArchLinux



Release date: 2019.01.17



Rel. 2.1



#

### Appunti per installare il sistema base: ##





```
loadkeys it
cfdisk
```

# Struttura delle partizioni:

```
/dev/sda1         # boot (flag bootable)
/dev/sda2         # root (/)
/dev/sda3         # Home
/dev/sda4         # Swap
```

# Creazione FileSystem:
```
mkfs.ext4 /dev/sda1
mkfs.ext4 /dev/sda2
mkfs.ext4 /dev/sda3
mkswap /dev/sda4
swapon /dev/sda4
```
# Montaggio partizioni e creazione cartelle:
```
mount /dev/sda2 /mnt
mkdir /mnt/boot /mnt/home
mount /dev/sda1 /mnt/boot
mount /dev/sda3 /mnt/home


# Monto la root (/dev/sda2 sotto /mnt) 
# Creo le cartelle /boot e /home nella partizione /dev/sda2 appena montata in /mnt
# Monto /dev/sda1 (partizione di boot) in /mnt/boot
# Monto /dev/sda3 (la partizione della home) in /mnt/home
```
# Installazione sistema base:
```
pacstrap /mnt base base-devel
```
# Generazione del file fstab e login chroot nel sistema appena installato:
```
genfstab -p /mnt >> /mnt/etc/fstab          # Genera il file in /etc/fstab
arch-chroot /mnt                            # Entro in chroot per modificare il sistema appena installato
```
# Lingua, Data/ora, hostname
```
vi /etc/locale.gen  # Decommenta sia it_IT.UTF-8 UTF-8 che en_US.UTF-8
locale-gen          # Genera il locale
echo "LANG=it_IT.UTF-8" > /etc/locale.conf
echo "LANG=it_IT.UTF-8\nKEYMAP=it" > /etc/vconsole.conf
export LANG=it_IT.UTF-8

rm /etc/localtime
ln -s /usr/share/zoneinfo/Europe/Rome /etc/localtime
hwclock --systohc --utc

echo "nome_pc" > /etc/hostname
vi /etc/hosts
                    # Inserire:
                                127.0.0.1   localhost.localdomain   localhost
                                ::1         localhost.localdomain   localhost
                                127.0.1.1   nome_pc.localdomain     nome_pc
```
