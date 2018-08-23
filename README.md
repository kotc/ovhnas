# ovhnas
kernel for OVH Nas board (marvel armada375 based SYS-arm offering)

## about
SoYouStart.com started offering cheap backup storage space, problem is, they have provided quite old kernel (initially 4.5.2) which worked well, but was.. old. later they did provide updated one (4.9.58) which was a bit newer, although still old and hitting kernel regression with network driver (resulting in very slow uploads ~4mbit/s). this project aims to provide newer, bug-fixed kernel and some system tweaks.

## state
WIP (work-in-progress). initial work on 4.9.123 is done, kernel boots, upload speeds reach ~1.6gbit/s inside ovh infra and ~500mbit/s outside. realistically you should expect a bit less if you use LUKS and/or rsync/sshfs. still you should notice an improvement. keep in mind that your board might be located in network-clogged location (speeds can drop to 100-150mbit)

## help
we need testers! join us on: irc://irc.freenode.com/sysarm (#sysarm on freenode network) to help testing things and/or donate to the project if you like it and feel thankful :)

## installation
for testers there is a script available at: http://54.37.26.148/kc375-update.sh join irc and ask for credentials
