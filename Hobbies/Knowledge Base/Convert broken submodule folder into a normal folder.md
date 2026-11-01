- Problem:
	- Situation: The project folder has a right arrow icon "=>" in the middle of the folder after pushing on Git
	- Reason: A cloned git repo folder that is pushed into the personal folder
	- Solution: Convert broken submodule folder into a normal folder

- Procedures:
	- Step 1: Stop tracking the folder as a shortcut
		```shell
		git rm --cached YOUR_FOLDER_NAME
		```
	- Step 2: Delete the hidden `.git` folder _inside_ that specific folder
		```shell
		rm -rf YOUR_FOLDER_NAME/.git
		```
	- Step 3: Add, commit, and push it back up
		```shell
		git add YOUR_FOLDER_NAME
		git commit -m "Fix: Converted broken submodule folder into a normal folder"
		git push origin main
		```