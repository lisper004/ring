# INSTALL.md

Welcome to the Lisper004's RING (Replos Is Not Guix) System installation wizard.

First, you have two options:
1) Build the ISO yourself
2) Download the latest ISO from [Release](https://github.com/lisper004/ring/releases/tag/0.1.1)

If you chose the first option
## Step 1) You need to install the ```archiso``` package
For Arch GNU/Linux:
```bash
sudo pacman -S archiso
```
Or:
```bash
yay -S archiso
```
In replos:
```scheme
(pm-install "archiso")
```
Or:
```scheme
(cmd "yay -S archiso")
```

No support for other distributions yet (will be available later via sh scripts)

## Step 2) Clone the repository and go to the folder
```bash
git clone https://github.com/lisper004/ring.git && cd ring/
```
## Step 3) Use ```mkarchiso```
```bash
sudo mkarchiso -v -w ./work -o ./out ./
```

mkarchiso will install all the necessary packages (and unnecessary ones, lol), and then create an ISO image using xorriso. You can later see it in the out/ folder.

## For USB
If you're on Windows, use Rufus or a similar utility.
On Linux, you can use the standard dd utility:
```bash
sudo dd if=out/ringreplos-*.iso of=/dev/sd? status=progress bs=4M && sync
```
Where's ```sd``` is your flash drive (check with ```lsblk``` or ```fdisk --list```)

## For QEMU
```bash
qemu-system-x86_64 -enable-kvm -cdrom /path/to/ring/out/ringreplos-*.iso -m 4G -boot d
```
where ``` /path/to/ring/out/ringreplos-*.iso``` is the path to the folder with the ISO (for example, /home/user/Downloads/ringreplos-*.iso)

After this, you will have a working ISO.
