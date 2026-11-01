1. Generate the transcript file in `json` format with timestamp using `faster-whisper`
	```shell
	faster-whisper -o Part_1.json --model_size_or_path base --device cpu --compute_type int8 Part\ 1.mp4
	```

2. Getting the content reference
	We need a reference to match the filenames of our videos to
	Create a `content.txt` file which contains the course content
	Say I'm following this course [TypeScript: From First Steps to Professional](https://master.dev/courses/typescript-first-steps/) , so the content that I need for the file `content.txt` is going to be
	```shell
	Introduction
	JavaScript Type Pitfalls
	Why TypeScript Matters
	What is TypeScript
	Install & Run TypeScript
	Fixing Errors Exercise
	TypeScript Syntax: Variables & Functions
	Arrays & Objects
	Union Types
	Type Narrowing, Guards, & Aliases
	Migrating from JavaScript to TypeScript
	Type Annotations Exercise
	Compiling TypeScript Files
	```

3. Create `split_chapters_part[].sh` using Claude
	1. Provide Claude with the `.json` transcript file we created in Step 1 and the `content.txt` file we created in Step 2
	2. Split video based on timestamps
		Claude prompt
		> Create cut points with the timestamps from the transcript file in `.json` and match the filenames from the `content.txt` file with the generated videos.
		The format in `.sh` file will look like this
		
		Example from `split_chapters_part1.sh`
		```shell
		#!/bin/bash
		# Usage: ./split_chapters_part1.sh "Part1.mp4" [accurate]
		IN="$1"
		MODE="${2:-fast}"
		[ -z "$IN" ] && { echo "Usage: $0 Part1.mp4 [accurate]"; exit 1; }
		OUT="chapters"
		mkdir -p "$OUT"
		
		cut() {  # cut <start_sec> <end_sec> <filename>
		  local s="$1" e="$2" name="$3"
		  local d; d=$(echo "$e - $s" | bc)
		  echo "→ $name"
		  if [ "$MODE" = "accurate" ]; then
		    ffmpeg -loglevel error -y -ss "$s" -i "$IN" -t "$d" -c:v h264_videotoolbox -b:v 6M -c:a aac -b:a 160k "$OUT/$name.mp4"
		  else
		    ffmpeg -loglevel error -y -ss "$s" -i "$IN" -t "$d" -c copy -avoid_negative_ts make_zero "$OUT/$name.mp4"
		  fi
		}
		
		#   start    end      name
		cut 0        1112.48  "01 - Introduction"
		cut 1117.48  2143.28  "02 - JavaScript Type Pitfalls"
		cut 2146.28  2518.28  "03 - Why TypeScript Matters"
		cut 2521.28  3698.08  "04 - What is TypeScript"
		
		echo "Done. Files are in ./$OUT"
		```

3. Generate the split videos
	- Scenario 1: We have one long video which consists of multiple chapters
		```shell
		#!/bin/bash
		# Usage: ./split_chapters_part2.sh "Part2.mp4" [accurate]
		IN="$1"
		MODE="${2:-fast}"
		[ -z "$IN" ] && { echo "Usage: $0 Part2.mp4 [accurate]"; exit 1; }
		OUT="chapters"
		mkdir -p "$OUT"
		
		cut() {  # cut <start_sec> <end_sec> <filename>
		  local s="$1" e="$2" name="$3"
		  local d; d=$(echo "$e - $s" | bc)
		  echo "→ $name"
		  if [ "$MODE" = "accurate" ]; then
		    ffmpeg -loglevel error -y -ss "$s" -i "$IN" -t "$d" -c:v h264_videotoolbox -b:v 6M -c:a aac -b:a 160k "$OUT/$name.mp4"
		  else
		    ffmpeg -loglevel error -y -ss "$s" -i "$IN" -t "$d" -c copy -avoid_negative_ts make_zero "$OUT/$name.mp4"
		  fi
		}
		
		#   start    end      name   (numbered in content.txt order, not video order)
		cut 245.00   1145.36  "01 - Making First Impressions"
		cut 3407.16  4229.16  "02 - Decoding Microexpressions"
		cut 1153.00  2205.16  "03 - Power Cues & Leadership Presence"
		cut 4236.16  4980.16  "04 - Voice Delivery & Control"
		cut 2206.16  3399.16  "05 - Trust & Warmth vs. Competence"
		
		echo "Done. Files are in ./$OUT"
		```
		We run the **sh** file with
		```shell
		./split_chapters.sh video.mp4
		```
		If the shell asks for permission
		```shell
		chmod +x split_chapters.sh split_chapters.sh
		```
		Then run the first line again
		```shell
		./split_chapters.sh video.mp4
		```
	- Scenario 2: We have multiples long videos and each of them has multiple chapters
	We're going to split the videos in chunks, each chunk consists of a couple of videos
		```shell
		#!/bin/bash
		# Runs the chapter scripts for "TypeScript First Steps" one after another (never in parallel).
		#
		# Usage:
		#   ./run_all_chapters.sh                  # all parts, fast mode (no re-encode)
		#   ./run_all_chapters.sh accurate         # all parts, frame-accurate cuts
		#   ./run_all_chapters.sh accurate 1 2 3   # only Parts 1, 2 and 3 (to work in chunks)
		#
		# Put this file, the split_chapters_partN.sh scripts and PartN.mp4 videos in the same folder.
		
		MODE="fast"
		if [ "$1" = "accurate" ]; then MODE="accurate"; shift; fi
		PARTS=("$@")
		[ ${#PARTS[@]} -eq 0 ] && PARTS=(1 2 3 4 5 6 7 8 9)
		
		for p in "${PARTS[@]}"; do
		  VIDEO="Part$p.mp4"
		  SCRIPT="./split_chapters_part$p.sh"
		  if [ ! -f "$VIDEO" ];  then echo "Skipping Part $p: $VIDEO not found"; continue; fi
		  if [ ! -f "$SCRIPT" ]; then echo "Skipping Part $p: $SCRIPT not found"; continue; fi
		  echo "=== Part $p ($MODE) ==="
		  bash "$SCRIPT" "$VIDEO" "$MODE" || { echo "Part $p failed, stopping."; exit 1; }
		done
		echo "All requested parts finished. Chapters are in ./chapters"
		```


3. Generated videos
	The videos that are split upon timestamps will be generated inside the folder **chapters**


## Pausing or Stopping and Rerunning later?
You can do either. Which one is better depends on how long the break is.

**Pausing (for a short break)**

- Press `Ctrl+Z` in the Terminal window to pause the script. It stays in memory, and Terminal prints something like `[1]+ Stopped`.
- Type `fg` and press Enter to resume exactly where it left off.
- This only works while that Terminal window stays open and the Mac stays on. Closing the window or shutting down ends the script.
- If the Mac goes to sleep, the script just pauses and normally resumes when you wake it. To prevent sleep during a long run, start it with `caffeinate -i`, like this:

```
  caffeinate -i ./run_all_chapters.sh accurate
```

**Stopping and rerunning (for a longer break)**

- Press `Ctrl+C` to stop it.
- Rerunning is safe. The scripts overwrite existing files (`-y`), so nothing breaks, but they start from the beginning and don't skip chapters that already finished.
- The chapter being cut when you stopped will be incomplete. The rerun overwrites it.
- Delete any files in the output folder whose names start with a dot (like `.06a.mp4`), which are leftover pieces from joined chapters.

**What I'd do**

- **For `run_all_chapters.sh`:** stop it with `Ctrl+C`, note which part it was on, then rerun from that part only. For example, if it stopped during Part 4:

```
  ./run_all_chapters.sh accurate 4 5 6 7 8 9
```

That avoids repeating Parts 1 to 3. If you're working in chunks, as I suggested earlier, you don't need to pause at all, since each chunk finishes on its own.

- **For a single script like `split_achieve_more.sh`:** it only makes seven cuts, so rerunning the whole thing is easiest. In fast mode it takes seconds.
- **If you only need a few chapters redone:** open the script and put `#` at the start of the `cut` lines you don't want to repeat. Commented lines are skipped.

Fast mode only copies the video, so stopping and restarting costs almost nothing. `accurate` mode re-encodes, so it's the one where pausing or restarting matters.

---


## Archive
2. Get cut points from transcript `json` - __confirmation needed__
	- Example of cut points
		```txt
		0 905 01_Introduction
		905 1560 02_Workshop_Setup
		1560 2916 03_Compiling_TypeScript_with_TSC
		2916 4124 04_Variable_Declarations_and_Inference
		4124 4390 05_Any_and_Type_Casting
		```
	- Create `chapters.txt` file to contain those cut points
		```shell
		cat > chapters.txt <<'EOF'
		0 905 01_Introduction
		905 1560 02_Workshop_Setup
		1560 2916 03_Compiling_TypeScript_with_TSC
		2916 4124 04_Variable_Declarations_and_Inference
		4124 4390 05_Any_and_Type_Casting
		EOF
		```
3. Split the video
	- Create the `split.sh` file
		```shell
		cat > split.sh <<'EOF'
		#!/bin/bash
		INPUT="Part 2.mp4"
		
		# Use tr to remove potential carriage returns (\r) from line endings
		tr -d '\r' < chapters.txt | while read -r start duration title || [ -n "$start" ]; do
		  # Skip blank lines or comments starting with #
		  [[ -z "$start" || "$start" =~ ^# ]] && continue
		
		  echo "Processing: $title (Start: $start, Duration: $duration)"
		
		  ffmpeg -nostdin -y -ss "$start" -t "$duration" -i "$INPUT" \
		    -c:v libx264 -crf 20 -c:a aac -movflags +faststart "${title}.mp4"
		done
		EOF
		```
	- Run the `split.sh` file
		```shell
		chmod +x split.sh
		./split.sh
		```
	> [!NOTE]
	> Change the `INPUT` accordingly

### Problem
Running this line
```shell
./split_chapters_part2_updated.sh "Part2.mp4" accurate
```
Give the problem:
`zsh: permission denied: ./split_chapters_part2_updated.sh`
Solution:
- Run this
	```shell
	chmod +x split_chapters_part2_updated.sh
	./split_chapters_part2_updated.sh
	```
	It will show
	```shell
	Usage: ./split_chapters_part2_updated.sh video.mp4 [accurate]
	```
- Then run this again
	```shell
	./split_chapters_part2_updated.sh "Part2.mp4" accurate
	```


Update
1. Create the **content.txt** file for the course content
2. Create **json** file for the transcript with the timestamps
3. Ask Claude for support with two tasks
	1. Find the cut points for the video by matching the timestamps
	2. Generate the 