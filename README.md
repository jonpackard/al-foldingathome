# al-foldingathome
# Steps to quickly set up Folding@Home on arch linux

pacman -Sy --needed base-devel git
useradd -m build
su - build
git clone https://aur.archlinux.org/foldingathome.git
cd foldingathome
makepkg
exit
pacman -U /home/build/foldingathome/foldingathome-*.pkg.tar.zst
pacman -S clinfo cuda ocl-icd opencl-driver #only if GPU folding
nano /etc/foldingathome/config.xml
systemctl start foldingathome
tail -f /var/log/foldingathome/log.txt
