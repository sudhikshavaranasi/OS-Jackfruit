# TEST CASES

## Test Case 1: chroot isolation

command:
sudo./engine start test ./rootfs-base /bin/pwd

output:
/

screenshot:
![pwd output](screenshots/pwd_output.png)

explanation: confirms process runs inside isolated root filesystem using chroot.

## Test case 2: command execution

command: 
sudo ./engine start alpha ./rootfs-base /bin/ls

screenshot:
![ls output](screenshots/ls_output.png)

explanation:
confirms commands run inside container


## Test Case 3: Multi-container supervision

command:
./program start c1 rootfs "pwd"
./program start c2 rootfs "pwd"

screenshot:
![multiple containers](screenshots/c1_rootfs_output.png)
![multiple containers](screenshots/c2_rootfs_output.png)


explanation:
demonstrates that the supervisor can manage multiple containers simultaneously under a single process.


## Test Case 4: CLI and IPC

command:
./program start c1 rootfs "pwd"

output:
Response: Started container c1 with PID XXXX

screenshot:
![ipc](screenshots/c1_rootfs_output.png)


explanation:
shows communication between CLI and supervisor via UNIX domain sockets.
