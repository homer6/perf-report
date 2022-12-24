# CPU or Code Path Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).

## bpftrace

```
# Programs started (execve) and their arguments
sudo bpftrace -e 'tracepoint:syscalls:sys_enter_execve { join(args->argv) }'

# Syscall count by program
bpftrace -e 'tracepoint:raw_syscalls:sys_enter { @[comm] = count(); }'

# Show per-second syscall rates:
bpftrace -e 'tracepoint:raw_syscalls:sys_enter { @ = count(); } interval:s:1 { print(@); clear(@); }'

# Count LLC cache misses by process name and PID (uses PMCs):
bpftrace -e 'hardware:cache-misses:1000000 { @[comm, pid] = count(); }'

# Profile user-level stacks at 99 Hertz, for PID 189:
bpftrace -e 'profile:hz:99 /pid == 189/ { @[ustack] = count(); }'

# Stack trace for application
bpftrace -e 'profile:hz:49 /comm == "chrome"/ { @[ustack] = count(); }'
```


## flamescope

```
git clone https://github.com/Netflix/flamescope
cd flamescope
docker build -t flamescope .

mkdir /tmp/profiles
sudo perf record -F 49 -a -g -- /home/user/your-executable --your-arg1 --your-arg2
sudo perf script --header > /tmp/profiles/test-01.profile

docker run --rm -it -v /tmp/profiles:/profiles:ro -p 5000:5000 flamescope
```