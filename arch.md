layout: page
title: "arch installation"
permalink: /arch

#Arch Linux Installation Information

1. download ISO from https://mirrors.mit.edu/archlinux/iso/2025.10.01/
2. verify ISO 
3. prepare vmware - Suffer for several hours, throw in the towel.
4. prepare VirtualBox (vmware made me Really Sad)
5. assign 2 cores, 4gib memory, and 32 gb drive space.
6. boot into arch 
7. check boot info, looks like my vm has BIOS as the default.
8. check network connection by pinging "ping.archlinux.com", network is active
9. check timezone using timedatectl
10. timezone is wrong, check list of timezones using "timedatectl list-timezones"
11. set timezone using "timedatectl set-timezone America/Chicago"
12. check name of my disk using "fdisk -l", disk is located at /dev/sda
13. open partitioner using "fdisk /dev/sda"
14. Create two partitions, the first partition being 4GB for SWAP, the second being 28GB for well. Everything Else^TM
15. write changes
16. setup sda1 as the swap space using "mkswap /dev/sda1"
17. setup sda2 as root using "mkfs.ext4 /dev/sda2"
18. mount sda2 using "mount /dev/sda2 /mnt"
19. enable swap using "swapon /dev/sda1"
20. don't change any of the mirrors, can't be bothered.
21. install essential packages using pacstrap -K /mnt base linux 
22. genfstab -U /mnt >> /mnt/etc/fstab - The wiki told me to!
23. arch-chroot /mnt - Change Root into the mount point
24. ln -sf /usr/share/zoneinfo/America/Chicago /etc/localtime - The wiki told me to!
25. hwclock --systohc - The wiki told me to! 
26. locale-gen
27. pacman -S nano - Install nano
28. nano /etc/locale.conf
29. LANG=en_US.UTF-8 - Configure locale info
30. SETUP NETWORK MANAGEMENT. DEAR GOD. - I forgot to install a network manager on my first go through of this. And also the second :)
31. pacman -S networkmanager
32. pacman -S sudo
33. passwd
34. nano /etc/hostname
35. pacman -S grub
36. grub-install --target=i386-pc /dev/sda - Install grub, targeted at a i386-pc, which is set that way because i'm using bios / mbr for my partition scheme.
37. grub-mkconfig -o /boot/grub/grub.cfg - make the grub config
38. exit - exit the chroot environment
39. reboot
40. login,
41. systemctl enable NetworkManager.service
42. systemctl start NetworkManager.service
43. pacman -S gnome
44. systemctl enable gdm.service - installing gnome so I can have a nice lil desktop environment 
45. reboot
46. add user lilly, add user lilly to wheel group, visudo, enable wheel group to do sudo stuff.
47. add user codi, add codi to wheel group.
48. sudo pacman -S git
49. sudo pacman -S base-devel
50. git clone https://aur.archlinux.org/rustrover.git
51. makepkg
52. pacman -U for all the package files
53. sudo pacman -S openssh - was already installed, updated it.
54. sudo passwd codi - password is "codipasswd"
55. sudo usermod -aG wheel codi
56. sudo pacman -S zsh
57. sudo chsh -s $(which zsh)
58. install oh my zsh
59. sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
60. nano .zshrc
61. git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
62. change the theme to "powerlevel10k/powerlevel10k"
63. install all the fonts for p10k https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#meslo-nerd-font-patched-for-powerlevel10k
64. change the font in the preferences bar for gnome term
65. run "p10k configure"
66. ???
67. profit


