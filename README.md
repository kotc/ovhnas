# ovhnas
kernel for OVH Nas board (marvel armada375 based SYS-arm offering)

## about
SoYouStart.com started offering cheap backup storage space, problem is, they have provided quite old kernel (initially 4.5.2) which worked well, but was.. old. later they did provide updated one (4.9.58) which was a bit newer, although still old and hitting kernel regression with network driver (resulting in very slow uploads ~4mbit/s). this project aims to provide newer, bug-fixed kernel and some system tweaks.

## state
WIP (work-in-progress). initial work on 4.9.119 is done, kernel boots, upload speeds reach ~1.6gbit/s inside ovh infra and ~500mbit/s outside.

## help
we need testers! join us on: irc://irc.freenode.com/sysarm (#sysarm on freenode network) to help testing things and/or donate to the project if you like it and feel thankful :)
