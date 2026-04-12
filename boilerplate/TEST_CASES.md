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

