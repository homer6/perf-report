# Network Analysis One-liners

Most of these are copied or adapted from Brendan Gregg's books, his website, or the [IO Visor Project](https://github.com/iovisor).

## bpftrace

```
# Count the connect syscall enter, by PID and command
bpftrace -e 't:syscalls:sys_enter_connect { @[pid, comm] = count(); }'

# Count the connect syscall enter, by command
bpftrace -e 't:syscalls:sys_enter_connect { @[comm] = count(); }'

# Count the connect syscall exit errors, by command and error code
bpftrace -e 't:syscalls:sys_exit_connect /args->ret < 0/ { @[comm, - args->ret ] = count(); }'

# Received bytes, by command
bpftrace -e 'kr:tcp_recvmsg /retval >= 0/ { @recv_bytes[comm] = hist(retval) }'
```