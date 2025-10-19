### Container related one-liners

Count syscalls per container:
```
bpftrace -e 't:syscalls:sys_enter_openat /cgroup == cgroupid("/sys/fs/cgroup/unified/container1")/ { printf ("%s\n", str(args->filename)); }'
```
