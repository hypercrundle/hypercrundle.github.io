---
layout: page
title: "arch installation"
permalink: /arch
---
#Arch Linux Installation Information

#Pre-Installation

1. download ISO from https://mirrors.mit.edu/archlinux/iso/2025.10.01/
2. verify ISO 
3. prepare vmware - Suffer for several hours, throw in the towel.
4. prepare VirtualBox (vmware made me Really Sad)
5. assign 2 cores, 4gib memory, and 32 gb drive space.
6. boot into arch

#Installation
  
8. check boot info, looks like my vm has BIOS as the default.
9. check network connection by pinging "ping.archlinux.com", network is active
10. check timezone using timedatectl
11. timezone is wrong, check list of timezones using "timedatectl list-timezones"
12. set timezone using "timedatectl set-timezone America/Chicago"
13. check name of my disk using "fdisk -l", disk is located at /dev/sda
14. open partitioner using "fdisk /dev/sda"
15. Create two partitions, the first partition being 4GB for SWAP, the second being 28GB for well. Everything Else^TM
16. write changes
17. setup sda1 as the swap space using "mkswap /dev/sda1"
18. setup sda2 as root using "mkfs.ext4 /dev/sda2"
19. mount sda2 using "mount /dev/sda2 /mnt"
20. enable swap using "swapon /dev/sda1"
21. don't change any of the mirrors, can't be bothered.
22. install essential packages using pacstrap -K /mnt base linux 
23. genfstab -U /mnt >> /mnt/etc/fstab - The wiki told me to!
24. arch-chroot /mnt - Change Root into the mount point
25. ln -sf /usr/share/zoneinfo/America/Chicago /etc/localtime - The wiki told me to!
26. hwclock --systohc - The wiki told me to! 
27. locale-gen
28. pacman -S nano - Install nano
29. nano /etc/locale.conf
30. LANG=en_US.UTF-8 - Configure locale info
31. SETUP NETWORK MANAGEMENT. DEAR GOD. - I forgot to install a network manager on my first go through of this. And also the second :)
32. pacman -S networkmanager
33. pacman -S sudo
34. passwd
35. nano /etc/hostname
36. pacman -S grub
37. grub-install --target=i386-pc /dev/sda - Install grub, targeted at a i386-pc, which is set that way because i'm using bios / mbr for my partition scheme.
38. grub-mkconfig -o /boot/grub/grub.cfg - make the grub config
39. exit - exit the chroot environment
40. reboot

#Post Installation


42. login,
43. systemctl enable NetworkManager.service
44. systemctl start NetworkManager.service
45. pacman -S gnome
46. systemctl enable gdm.service - installing gnome so I can have a nice lil desktop environment 
47. reboot
48. add user lilly, add user lilly to wheel group, visudo, enable wheel group to do sudo stuff.
49. add user codi, add codi to wheel group.
50. sudo pacman -S git
51. sudo pacman -S base-devel
52. git clone https://aur.archlinux.org/rustrover.git
53. makepkg
54. pacman -U for all the package files
55. sudo pacman -S openssh - was already installed, updated it.
56. sudo passwd codi - password is "codipasswd"
57. sudo usermod -aG wheel codi
58. sudo pacman -S zsh
59. sudo chsh -s $(which zsh)
60. install oh my zsh
61. sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
62. nano .zshrc - add some fun aliases :D
63. git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
64. change the theme to "powerlevel10k/powerlevel10k"
65. install all the fonts for p10k https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#meslo-nerd-font-patched-for-powerlevel10k
66. change the font in the preferences bar for gnome term
67. run "p10k configure"
68. ???
69. profit


