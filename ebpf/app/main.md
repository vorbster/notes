### App related one-liners

Count mutex lock functions:
```
bpftrace -e 'u:/usr/lib64/libpthread.so.0:pthread_mutex_*lock { @probe = count(); } interval:s:1 { exit(); }'
```

Currently no way to trace spinlocks with bpftrace.
But you can funccount them:
```
funccount '*spin_lock*'
```

Count LLC misses per process:
```
bpftrace -e 'hardware:cache-misses:1000000 {@[comm] = count(); }'
```

Profile user-level stacks at 99 Hertz for PID 189:
```
bpftrace -e 'profile:hz:99 /pid == 189/ { @[ustack] = count(); }'
```
