# ovhnas
kernel for OVH Nas board (marvel armada375 based SYS-arm offering, running at 800MHz).

## about
SoYouStart.com started offering cheap backup storage space, problem is, they have provided quite old kernel (initially 4.5.2) which worked well, but was.. old. later they did provide updated one (4.9.58) which was a bit newer, although still old and hitting kernel regression with network driver (resulting in very slow uploads ~4mbit/s). recently (2018-08) they have updated the kernel to 4.9.124, which is nice regarding security, but still having slow uploads bug. this project aims to provide newer, bug-fixed kernel and some system tweaks.

## state: WIP (work-in-progress)
- initial work on 4.9.126 is done, kernel boots, upload speeds reach ~2.3gbit/s inside ovh infra and ~300mbit/s outside. realistically you should expect a bit less if you use LUKS and/or rsync/sshfs. still you should notice an improvement. keep in mind that your board might be located in network-clogged location (speeds can drop to 100-150mbit)
- also ported to 4.14.69
- cryptodev: WORKS
- luks + hwcrypto: WORKS
- ssh/sshd + hwcrypto: WORKS, install or recompile openssl lib. for debian9 it needs to be openssl-1.0
- wireguard: WORKS
- ipv6: works with tunnels. for native, sys/ovh needs to enable ipv6 routing on their routers

## help
we need testers! join us on: irc://irc.freenode.com/sysarm (#sysarm on freenode network, you can also use web interface at: http://webchat.freenode.net/?channels=#SYSarm) to _help testing_ and/or _donate_ to the project (https://www.paypal.me/kotc) if you like it and feel thankful :)

## installation
for testers there is a script available at: http://54.37.26.148/kc375-update.sh join irc and ask for credentials

## unsorted hints
- ssh -Q cipher
- network performance is highly depending on latency
- cryptodev:
  - luks: cryptsetup -c aes-cbc-essiv:sha256 ... (less safe, but ok for single user machine)
- openssl(1.0/1.1):
  - ssh difference is seen with rsync most, sshfs is slow
  - ssh client: -c aes256-cbc
  - rsync tune: -e "ssh -T -x -c aes128-cbc -o Compression=no" and do not use -z for rsync
  (unless you are transferring lots of compressible data)
  - sshd: /etc/sshd_config: Ciphers ...
  - openssl compiled with both cryptos and digests is triggering oops so dont use.

## TODO
- benchmarks in different usage scenarios (ie. with/without hwcrypto, luks, ssh/rsync). initial quick and dirty comparison is at http://54.37.26.148/kc375-bench/bench-all.php
