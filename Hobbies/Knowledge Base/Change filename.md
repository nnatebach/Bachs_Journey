Change all filenames that contain "*_subbed.mp4" to "*.mp4"
- In the current directory
	``` shell
	for file in *_subbed.mp4; do mv "$file" "${file/_subbed.mp4/.mp4}"; done
	```
	
	| From                       | To                  |
	| -------------------------- | ------------------- |
	| 1. Introduction_subbed.mp4 | 1. Introduction.mp4 |
- From the main directory to all the sub-directories
	```bash
	find . -type f -name "*_subbed.mp4" | while read -r file; do
	    mv "$file" "${file/_subbed.mp4/.mp4}"
	done
	```
	