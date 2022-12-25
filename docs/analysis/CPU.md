# CPU or Code Path Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).


## common

```
# system at a glance; press c to show command arguments
htop

# load averages (1 minute, 5 minute, 15 minute) for runnable or IO-blocked
uptime

# check for system errors (eg. oom-killed, TCP drops)
dmesg | tail

# show running and runnable tasks, cpu idle
vmstat 1

# see idle, per cpu
mpstat -P ALL 1

# see running process (tasks), and their average CPU usage
pidstat 1

# sample all processes with perf top
perf top -F 49 -ns comm,dso -d 10 -g -z --source --children
```


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

# Count context switches, by command (this output looks wrong)
bpftrace -e 'software:context-switches { @[comm] = count(); }'

# Count context switches, by command
bpftrace -e 'tracepoint:sched:sched_switch { @[comm] = count(); }'

# Count cpu migrations, by command
bpftrace -e 'software:cpu-migrations { @[comm] = count(); }'
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


## perf

So many examples from [Brendan Gregg's homepage's perf examples](https://www.brendangregg.com/perf.html#UsageExamples).

See Chapter 13 from [Systems Performance](https://www.brendangregg.com/systems-performance-2nd-edition-book.html).

[Official perf wiki](https://perf.wiki.kernel.org/index.php/Main_Page).

```
perf record -F 99 -g
perf report -n --children -g

perf record -F 99
perf report -ns comm,dso -v
```