- Single File Conversion (Fast Remux without Re-encoding)

	If you want to change the container from `.ts` to `.mp4` instantly without losing quality or re-encoding the video/audio streams, run: [[1](https://apps.microsoft.com/detail/9p162bbmxncn?hl=vi-VN&gl=LU)]
	
	bash
	
	```bash
	ffmpeg -i input.ts -c copy output.mp4
	```
	
	Use code with caution.
	
	_(Replace `input.ts` with your source file name and `output.mp4` with your desired file name)._

---

- Batch Conversion for All `.ts` Files in a Folder

	To convert every `.ts` file in your current directory to `.mp4` at once, open Terminal, navigate to your folder using `cd /path/to/folder`, and run: [[1](https://www.reddit.com/r/ffmpeg/comments/16ivvaa/cant_batch_convert_ts_to_mp4_in_mac/)]
	
	bash
	
	```bash
	for f in *.ts; do ffmpeg -v quiet -i "$f" -c:v copy -an "${f%.*}.mp4"; done
	```
	
	Use code with caution.
	
	> [!NOTE]
	> If your `.ts` files contain audio that needs to be copied rather than dropped, use `-c copy` instead of `-c:v copy -an`):
	
	bash
	
	```bash
	for f in *.ts; do ffmpeg -i "$f" -c copy "${f%.*}.mp4"; done
	```
	
	Use code with caution.
	
	If you run into any issues (such as audio sync problems or unsupported codecs), let me know if you need to **re-encode the video** or **merge multiple `.ts` parts** together.