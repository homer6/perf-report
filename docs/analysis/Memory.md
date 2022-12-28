# Memory Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).


## sysstat

```
# show free memory and any swapping
vmstat 1

# show free memory
free -m
```


## bpftrace

```
# Count page faults, by command
bpftrace -e 'software:faults:1 { @[comm] = count(); }'

# Count minor faults, by command
bpftrace -e 'software:minor-faults { @[comm] = count(); }'

# Count major faults, by command
bpftrace -e 'software:major-faults { @[comm] = count(); }'

# Count page faults, by command
bpftrace -e 'tracepoint:exceptions:page_fault_user { @[comm] = count(); }'

# Count LLC cache misses, by command and PID (uses PMCs):
bpftrace -e 'hardware:cache-misses:1000000 { @[comm, pid] = count(); }'

# Heap expansion, by command
bpftrace -e 'tracepoint:syscalls:sys_enter_brk { @[comm] = count(); }'

# Memory allocation calls (bytes) by command, pid, user-space stack pointer (stats)
bpftrace -e 'tracepoint:kmem:kmalloc,tracepoint:kmem:kmem_cache_alloc { @bytes[comm, pid, ustack] = stats(args->bytes_alloc); }'

# Memory allocation calls (bytes) by command, pid, user-space stack pointer, filtered by pid (histogram)
bpftrace -e 'tracepoint:kmem:kmalloc,tracepoint:kmem:kmem_cache_alloc /pid == 189/ { @bytes[comm, pid, ustack] = hist(args->bytes_alloc); }'
```