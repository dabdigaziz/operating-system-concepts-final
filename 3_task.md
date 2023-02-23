
Before starting, our kernel module is

Step 1. Set-up the environment
Download Kernel 5.16.9 source code
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.16.9.tar.xz
Step 1.2. Extract xz file
unxz -v linux-5.16.9.tar.xz
Step 1.3. Verify sign key
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.16.9.tar.sign
gpg --verify linux-5.16.9.tar.sign

Step 1.4. Set-up recovery key
gpg --recv-keys 79BE3E4300411886

Step 1.5. Extract tar file
tar xvf linux-5.16.9.tar

Step 1.6. Configure the Linux kernel features and modules
cd linux-5.16.9
cp -v /boot/config-$(uname -r) .config

Step 2. Install the required compilers and other tools
sudo apt-get install build-essential libncurses-dev bison flex libssl-dev libelf-dev

Step 3. Configuring the kernel module
	make menuconfig


Step 4. Compile the kernel module
make -j $(nproc)
	
Step 5. Install the Kernel Linux module
sudo make modules_install


Step 6. Install the Linux Kernel
sudo make install


Step 7. Update grub config
sudo update-initramfs -c -k 5.16.9
sudo update-grub

Step 8. Reboot and run by new kernel

Successfully our kernel module is upgraded to our custom module
