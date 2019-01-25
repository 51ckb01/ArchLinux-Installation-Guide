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
## Struttura delle partizioni:
```
/dev/sda1         # boot (flag bootable)
/dev/sda2         # root(/)
/dev/sda3         # Home
```

Per aggiungere partizione di swap crea una quarta partizione (in questo caso `/dev/sda4`)

Formatta: `mkswap /dev/sda4` e abilita la swap con `swapon /dev/sda4`.

