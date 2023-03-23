# bcc-bpftrace-gadgets

## Usage
You need to install BCC and bpftrace first:
### For Ubuntu
```bash
# Install BCC
# Option1: Install at /sbin
sudo apt-get install bpfcc-tools linux-headers-$(uname -r)
# Option2: Install at /usr/share/bcc/tools
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4052245BD4284CDD
echo "deb https://repo.iovisor.org/apt/$(lsb_release -cs) $(lsb_release -cs) main"|\
  sudo tee /etc/apt/sources.list.d/iovisor.list
sudo apt-get-update
sudo apt-get install bcc-tools libbcc-examples linux-headers-$(uname -r)

# Option3: Install at /snap/bin
sudo snap install bcc

# Install bpftrace
# Option1: Install at /sbin
sudo apt-get update
sudo apt-get install bpftrace
```

### For RHEL
```bash
# Install BCC
# Option1: Install at /usr/share/bcc/tools
sudo yum install bcc-tools

# Install bpftrace
# Install at /usr/share/bpftrace/tools
sudo yum install bpftrace
```

After installing above, you should be able to run scripts in this repository.

You may also want to use flamegraph to do profiling. Flamegraph can be downloaded with:
```bash
git clone https://github.com/brendangregg/Flamegraph
```

To draw a flamegraph, do:
```bash
profile-new -af 30 -F 99 -p <PIDs> > out.stack
flamegraph.pl --color=java < out.stack > out.svg
```

It is recommended to add directories of installed BCC scripts, installed bpftrace scripts, downloaded flamegraph, and this repository to $PATH.
