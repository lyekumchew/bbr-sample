# Useage

```
# install the new kernel
$ dpkg -i linux-image-5.4.0-rc6_5.4.0-rc6-1_amd64.deb linux-headers-5.4.0-rc6_5.4.0-rc6-1_amd64.deb

# new kernel loading
$ update-grub && reboot

# enable bbrv2 with fq qdisc
$ echo "net.core.default_qdisc = fq" >> /etc/sysctl.conf
$ echo "net.ipv4.tcp_congestion_control = bbr2" >> /etc/sysctl.conf
$ sysctl -p

# ensure bbrv2 insmod kernel, if the output has the bbr2 keyword that means it's ok
# sysctl net.ipv4.tcp_available_congestion_control

# enable ECN (optional)
$ echo "net.ipv4.tcp_ecn = 1" >> /etc/sysctl.conf
$ echo "net.ipv4.tcp_ecn_fallback = 1" >> /etc/sysctl.conf
$ sysctl -p

# if having the following output, bbrv2 is running
# may be different from your output
$ lsmod | grep bbr
tcp_bbr                20480  2
```
