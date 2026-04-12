# Mini Container Runtime with Kernel Monitor

## Overview
This project implements a lightweight container runtime in user space along with a kernel module for monitoring container processes.

---

## Components

### 1. User-Space Runtime (engine.c)
- Launches isolated containers using `fork` and `chroot`
- Executes commands inside the container
- Sends container PID to kernel module using `ioctl`

### 2. Kernel Monitor (monitor.c)
- Linux Kernel Module (LKM)
- Creates device: `/dev/container_monitor`
- Receives PIDs from user-space via `ioctl`
- Stores processes in a linked list
- Uses mutex for safe access

---

## Features
- Container isolation using `chroot`
- User-space to kernel-space communication via `ioctl`
- Process tracking using linked list in kernel
- Lock-protected shared data structure

---

## Test Cases

### Test Case 1: Container Execution
Command:
sudo ./engine start test ./rootfs-base /bin/pwd

Output:
/

---

### Test Case 2: Kernel Integration
Command:
sudo ./engine start test ./rootfs-base /bin/pwd
sudo dmesg | tail

Output:
Monitor: Added PID XXXX

---

## How to Run

### Compile kernel module:
make

### Load module:
sudo insmod monitor.ko

### Run container:
sudo ./engine start test ./rootfs-base /bin/pwd

### Check logs:
sudo dmesg | tail

### Remove module:
sudo rmmod monitor

---

## Notes
- Memory usage tracking is simplified for demonstration
- Soft and hard limits can be extended further

---

## Conclusion
This project demonstrates integration between user-space and kernel-space for container monitoring using system-level programming concepts.
