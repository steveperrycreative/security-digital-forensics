| Regripper                                                                                   | Notes                              | 
|---------------------------------------------------------------------------------------------|------------------------------------| 
| perl rip.pl -r /mnt/Documents\ and\ Settings/{USER}/NTUSER.DAT -f ntuser > nt_user_out.csv  | Extract data from NTUSER.DAT file  | 
| perl rip.pl -r /mnt/WINDOWS/system32/config/SAM -f sam > sam_out.csv                        | As above but for the SAM hive      | 
| perl rip.pl -r /mnt/WINDOWS/system32/config/system -f system > system_out.csv               | As above but for the system hive   | 
| perl rip.pl -r /mnt/WINDOWS/system32/config/software -f software > software_out.csv         | As above but for the software hive | 
