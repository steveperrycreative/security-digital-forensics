| Command                                                                       | Notes                                                                                                            | 
|-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------| 
| md5sum myfile.txt                                                             | Hash file                                                                                                        | 
| md5deep mydir                                                                 | Hash all files in dir                                                                                            | 
| sha512sum                                                                     | Hash file                                                                                                        | 
| cmp file1 file2                                                               | Run a diff on the two files                                                                                      | 
| mount /dev/sda1 /mnt                                                          | Mount partition 1 to /mnt. Run with sudo                                                                         | 
| umount /dev/sda1                                                              | Unmount /dev/sda1                                                                                                | 
| umount /mnt                                                                   | As above                                                                                                         | 
| losetup /dev/loop0 /images/image.dd                                           | Create a loop device so that we can mount a disk image                                                           | 
| losetup /dev/loop0 /images/image.dd -o 1048576                                | As above but mounting a partition. The offset is blocks * block size (eg 2048 * 512)                             | 
| mount /dev/loop0 /mnt -o ro                                                   | Mount the above loop device in read only format (must use -o ro)                                                 | 
| umount /dev/loop0                                                             | Unmount the loop device                                                                                          | 
| losetup -d /dev/loop0                                                         | Delete the loop device                                                                                           | 
| dd if=/dev/zero of=/root/changes bs=512 seek=4095 count=1                     | Create a sparse file ready for snapshots. This eg creates a 2mb file that is only 4kb and will hold our changes. | 
| losetup /dev/loop1 /root/changes                                              | Create a loop device from the sparse file                                                                        | 
| blockdev --getsz /dev/loop0                                                   | Get the block size of the image                                                                                  | 
| dmsetup create sandbox --table "0 THESIZE snapshot /dev/loop0 /dev/loop1 N 1" | Create the snapshot. THESIZE is the size reported back from blockdev                                             | 
| mount /dev/mapper/sandbox /mnt                                                | Mount the snapshot. May need to "sync" after copying files to it by just running $ sync                          | 
| dmsetup remove sandbox                                                        | Remove the sandbox                                                                                               | 
