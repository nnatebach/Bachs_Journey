We want to make these
``` shell
43-Code to Website Overview.mp4
42-code-to-website-overview.vtt
```
Become these
``` shell
43-Code to Website Overview.mp4
43-Code to Website Overview.vtt
```
The point is to soft embed the subtitle file (vtt) into the video file (mp4)

The code
``` shell
for f in *.mp4; do name="${f%.mp4}"; keyword=$(echo "$name" | tr -cd '[:alpha:]' | tr '[:upper:]' '[:lower:]'); for v in *.vtt; do if echo "$v" | tr -cd '[:alpha:]' | tr '[:upper:]' '[:lower:]' | grep -q "$keyword"; then mv "$v" "$name.vtt"; break; fi; done; done
```
