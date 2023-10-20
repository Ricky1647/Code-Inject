### Run KVM Host

```
./run-kvm.sh -k ./linux/arch/arm64/boot/Image -i ./cloud_1.img
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


