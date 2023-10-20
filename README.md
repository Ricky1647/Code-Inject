### Run KVM Host
* follow the instructions to create an Ubuntu 20.04 virtual disk image
```
# qemu-img create -f raw cloud.img 25g
# mkfs.ext4 cloud.img
# mount cloud.img /mnt
# tar xvf ./ubuntu-20.04-server-cloudimg-arm64-root.tar.xz -C /mnt
# sync
# sudo touch /mnt/etc/cloud/cloud-init.disabled
```
* run kvm host
```
./run-kvm.sh -k ./linux/arch/arm64/boot/Image -i ./cloud.img
```

### Run gust 
* Enter guest vm
```
./run-guest.sh -k ./Image -i ./guest.img
```
* running target program
    * while-loop process waits for injecting code.
    * get GPA(Guest Physical Address) of text section.
```
./sheep
./top # check this process ${PID}
./page-types -p ${PID} -L
```

### Excute injecting code in KVM Host
* Input Guest Physical Address, and KVM will write guest physical memory.
* The while-loop prcoess change to shell process.
```
./inject
```


