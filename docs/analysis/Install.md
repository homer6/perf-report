# Installing Tools

## Amazon Linux 2

```
sudo yum install perf htop sysstat git -y
sudo yum install bpftrace -y
sudo amazon-linux-extras install BCC
git clone https://github.com/iovisor/bcc.git
git clone https://github.com/iovisor/bpftrace.git

cd bpftrace/tools
sudo ./runqlat.bt
```


## Ubuntu 22

```
sudo apt update
sudo apt install bpfcc-tools linux-headers-$(uname -r) git htop sysstat -y
git clone https://github.com/iovisor/bcc.git
git clone https://github.com/iovisor/bpftrace.git

cd bpftrace/tools
sudo ./runqlat.bt
```

