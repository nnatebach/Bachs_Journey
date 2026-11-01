- Check for the date and time of creation of a file
	```shell
	ls -lh [filename]
	```
- Create **and** switch to new branch
	- Traditional way
		```shell
		git checkout -b your-new-branch-name
		```
	- Modern way
		```shell
		git switch -c your-new-branch-name
		```
- Only create
	```shell
	git branch new-branch-name
	```
- Switch to existing branch
	- Traditional way
		```shell
		git checkout your-new-branch-name
		```
	- Modern way
		```shell
		git switch your-new-branch-name
		```
- Temporarily save uncommitted changes
	```shell
	git stash
	```
	==**temporarily shelves (saves) uncommitted changes** (both staged and unstaged) in your working directory== so you can work on something else, leaving you with a clean working directory.

> [!TIP]
> Use **`[upd]`** (update) if you modified or improved the existing Account Menu component, and use **`[add]`** if you introduced a completely new feature, file, or standalone menu option.