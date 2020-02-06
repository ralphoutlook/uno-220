Create Raspbian Image for UNO-220
===

### Prerequisite
---
- **[Raspberry pi 4 model b](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/)**
- **Advantech UNO-220 (IO extender)**
- **SD card (over 8GB recommanded)**

### UNO-220 Information
---
- **TI TCA9554 IO extender**  
- **RTC RX-8010SJ-B**
- **Serial to RS-232/485** 

### Download Raspbian Debian Buster Full Image
---
- **Download Image**
  ```
  $ curl -o 2019-09-26-raspbian-buster-full.zip http://downloads.raspberrypi.org/raspbian_full/images/raspbian_full-2019-09-30/2019-09-26-raspbian-buster-full.zip 
  $ unzip 2019-09-26-raspbian-buster-full.zip
  ```
- **Use `fdisk` command to check disk partitions.**
  ```
  $ fdisk -l 2019-09-26-raspbian-buster-full.img
  Disk 2019-09-26-raspbian-buster-full.img: 6.4 GiB, 6811549696 bytes, 13303808 sectors
  Units: sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disklabel type: dos
  Disk identifier: 0x5e3da3da

  Device                               Boot  Start      End  Sectors  Size Id Type
  2019-09-26-raspbian-buster-full.img1        8192   532479   524288  256M  c W95 FAT32 (LBA)
  2019-09-26-raspbian-buster-full.img2      532480 13303807 12771328  6.1G 83 Linux

  ```

### Raspbian Image Compiler and Kernel Source
---
- [Kernel Source](https://github.com/raspberrypi/linux.git)
- [Toolchain](https://github.com/raspberrypi/tools.git)


### Compile RTC Driver
---
- **Clone `project/iocard` from github repository.**

  ```
  $ git clone --depth 1 -b prject/iocard https://github.com/Advantech-IIoT/uno-220.git
  $ cd build/kernel
  $ make modules
  ```

- **Then, rtc driver will be located in the path as below.**
  ```
  $ ls build/modules/rtc/rtc-rx8010.ko
  build/modules/rtc/rtc-rx8010.ko
  ```