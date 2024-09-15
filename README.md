
# Containerd

There is the list of differences between this repo and `containerd/containerd`:

- [release 1.7.22] Fix missing ABI specification in the default apparmor profile.
- - On the default Debian 12 kernel everything works fine,
    but when installing proxmox kernel containers can no longer create unix sockets,
    which turns out to be an apparmor issue.
    When I created a very simple apparmor profile that allows everything, I also got "permission denied".
    But `aa-genprof` successfully created a working profile, with the main difference being `abi <abi/3.0>,` in the first line.
    Adding this line to the containerd profile also seems to fix the issue.
