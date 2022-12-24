# Memory Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).

## bpftrace

```
# Count page faults by process
bpftrace -e 'software:faults:1 { @[comm] = count(); }'

# Count LLC cache misses by process name and PID (uses PMCs):
bpftrace -e 'hardware:cache-misses:1000000 { @[comm, pid] = count(); }'
```