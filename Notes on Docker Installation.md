- There's Docker Desktop and Docker Engine
- Docker Desktop requires KVM which is used for hardware virtualization since docker desktop uses a VM to create its containers. The docker daemon runs in the VM.
- Docker Engine and Docker Desktop can run together though there may be issues sometimes with port sharing. [rimelek](https://forums.docker.com/t/difference-between-docker-desktop-and-docker-engine/124612) gives a nice difference between the two. Docker dektop practically tries to make the experience uniform between Mac, Windows and Linux users and that's why it uses a VM.
- Not all CPUs can run KVM since they don't support virtualization. For some reason mine doesn't (intel i5-7300HQ).
- - Check if CPU supports virtualization run: `egrep -c '(vmx|svm)' /proc/cpuinfo`. If the command returns 0, it means virtualization is not supported.
  - You could check if maybe virtualization needs to be enabled in the BIOS.
  - Find info on installing KVM [here](https://phoenixnap.com/kb/ubuntu-install-kvm).


