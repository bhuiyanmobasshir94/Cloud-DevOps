# Cloud DevOps

## Linux Commands Directory

## 5 commands to check memory usage on Linux
Ref: [Resource](https://www.binarytides.com/linux-command-check-memory-usage/) 
```
$ free -m
$ cat /proc/meminfo
$ vmstat -s
$ top
$ htop
```

## 16 Commands to Check Hardware Information on Linux
Ref: [Resource](https://www.binarytides.com/linux-commands-hardware-info/)

#### CPU
```
$ cat /proc/cpuinfo
```
#### Memory :
```
$ free
$ cat /proc/meminfo
```
#### HDD:
```
$ df -h
$ sudo fdisk -l
$ hdparm -i /dev/device (for example sda1, hda3...)
```
Ref: [Resource](https://serverfault.com/questions/112542/how-can-i-get-processor-ram-disk-specs-from-the-linux-command-line)

### Nvidia
```
nvidia-smi
```
Ref: [Resource](https://unix.stackexchange.com/questions/38560/gpu-usage-monitoring-cuda)

### Power Supply
```
sudo lshw -c power
```
Ref: [Resource](https://askubuntu.com/questions/1009423/find-the-power-supply-hardware-information-for-a-pc-using-ubuntus-command-line)

### Nvidia driver installation 

Ref: [Resource](https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/)
