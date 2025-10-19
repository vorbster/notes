### Commands that help to trace CPU related events 

Show who is executing what:

```
bpftrace -e 't:syscalls:sys_enter_execve { printf ("-> %s\n", str(args->filename))}'
```
