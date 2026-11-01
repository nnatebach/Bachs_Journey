- Copy and paste
	```shell
	cp ~/Movies/my_video.mp4 ~/Desktop/my_video_copy.mp4
	```
- Cut and paste
	```
	mv ~/Movies/my_video.mp4 ~/Desktop/my_video.mp4
	```
- In addition
	- Copying folders
		```shell
		cp -R ~/Documents/MyFolder ~/Desktop/MyFolder_Copy
		```
	- Moving folders
		```shell
		mv ~/Documents/MyFolder ~/Desktop/MyFolder
		```
> [!IMPORTANT]
> For moving folders, you don't need any extra flags

- Without progress bar
	``` shell
	mv source_file destination/
	```
- With progress bar
	``` shell
	rsync -avh --progress /path/to/source/folder/ /path/to/destination/folder/
	```
