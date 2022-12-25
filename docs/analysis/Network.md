# Network Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).


## common

```
# check network interface throughput
sar -n DEV 1

# number of locally initiated connections (active/connect) per second, remotely (passive/accept), retrans
sar -n TCP,ETCP 1
```


## bpftrace

```
# Count the connect syscall enter, by PID and command
bpftrace -e 't:syscalls:sys_enter_connect { @[pid, comm] = count(); }'

# Count the connect syscall enter, by command
bpftrace -e 't:syscalls:sys_enter_connect { @[comm] = count(); }'

# Count the connect syscall exit errors, by command and error code
bpftrace -e 't:syscalls:sys_exit_connect /args->ret < 0/ { @[comm, - args->ret ] = count(); }'

# Count the accept syscall enter, by command
bpftrace -e 't:syscalls:sys_enter_accept { @[comm] = count(); }'

# Received bytes, by command
bpftrace -e 'kr:tcp_recvmsg /retval >= 0/ { @recv_bytes[comm] = hist(retval) }'

# Sent bytes size histogram, by command
bpftrace -e 'k:tcp_sendmsg { @send_bytes[comm] = hist(arg2); }'

# Received bytes size histogram, by command
bpftrace -e 'k:tcp_recvmsg { @send_bytes[comm] = hist(arg2); }'

# Sent/received bytes size histogram, by command
bpftrace -e 'k:tcp_sendmsg,k:tcp_recvmsg { @send_bytes[func, comm] = hist(arg2); }'

# Count TCP send/receives by on-CPU PID and command
bpftrace -e 'k:tcp_sendmsg,k:tcp_recvmsg { @[func, pid, comm] = count(); }'

# Count all TCP probes by command
bpftrace -e 't:tcp* { @[probe, comm] = count(); }'

# Show distribution of size of tcp messages sent
bpftrace -e 'k:tcp_sendmsg { @size = hist(arg2); } interval:s:10 { exit(); }'
```