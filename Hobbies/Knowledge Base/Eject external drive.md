- Mac
	1. Check drive
		```shell
		diskutil list
		```
	Look for your drive under the `NAME` column or find its identifier (e.g., `disk2`).
	2. Eject the drive
		```shell
		diskutil eject /dev/disk2
		```
- Linux
	1. List and check the connected drive
		```shell
		lsblk
		```
	2. Eject the drive
		```shell
		udisksctl power-off -b /dev/sdb
		```