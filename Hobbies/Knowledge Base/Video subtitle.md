- Tools:
	- whisper
	- Faster-whisper
	- ffmpeg
- Audio format file: wav
- Subtitle format file: vtt
- Technique: Soft embed

## Instruction
**Step 1: Extract audio from video**
- Single file (studio quality wav file)
	```shell
	ffmpeg -i input.mp4 -vn -c:a pcm_s24le -ar 48000 -ac 2 output.wav
	```
- Multiple files
	``` c
	for file in *.mp4; do 
	 ffmpeg -i "$file" -vn -c:a pcm_s24le -ar 48000 "${file%.mp4}.wav"
	done
	```
> [!TIP]
> If you want to specify the language for the extracted file,
> add `-map 0:a:m:language:eng \`
> 

	Below is an example to extract `flac` file from an `mp4` file
	```shell
	for file in *.mp4; do
	    ffmpeg -i "$file" \
	        -map 0:a:m:language:eng \
	        -vn -c:a flac \
	        "${file%.mp4}.flac"
	done
	```

**Result**
![[Pasted image 20260724165222.png|291]]

**Step 2: Generate subtitle files (vtt) from audio files (wav)**
**2.1. Install whisper / faster-whisper**
**2.2. Script for generating vtt files**
- For single file
	```shell
	python3 -c "import faster_whisper; w='myaudio.wav'; m=faster_whisper.WhisperModel('small', device='cpu', compute_type='int8'); open(w.rsplit('.',1)[0]+'.vtt','w',encoding='utf-8').write('WEBVTT\n\n'+''.join(f'{int(s.start//3600):02d}:{int((s.start%3600)//60):02d}:{s.start%60:06.3f} --> {int(s.end//3600):02d}:{int((s.end%3600)//60):02d}:{s.end%60:06.3f}\n{s.text.strip()}\n\n' for s in m.transcribe(w, language='en', vad_filter=True)[0]))"
	```
- From the beginning

	``` python
	import os
	import glob
	from faster_whisper import WhisperModel
	
	# 1. Initialize the model on CPU (Optimized for Mac architecture)
	model_size = "base"
	model = WhisperModel(model_size, device="cpu", compute_type="float32")
	
	# 2. Find all WAV files
	wav_files = glob.glob("*.wav")
	
	if not wav_files:
	    print("No .wav files found in this directory.")
	    exit()
	
	for wav_path in wav_files:
	    # Set up the VTT filename
	    base_name = os.path.splitext(wav_path)[0]
	    vtt_path = f"{base_name}.vtt"
	
	    print(f"Transcribing (Fresh Start): {wav_path}...")
	
	    # 3. Process the audio
	    segments, info = model.transcribe(wav_path, language="en")
	
	    # 4. Save and overwrite the VTT file
	    with open(vtt_path, "w", encoding="utf-8") as f:
	        f.write("WEBVTT\n\n")
	
	        for segment in segments:
	            # Format timestamps to HH:MM:SS.mmm
	            start_h, start_m, start_s = int(segment.start//3600), int((segment.start%3600)//60), segment.start%60
	            end_h, end_m, end_s = int(segment.end//3600), int((segment.end%3600)//60), segment.end%60
	
	            start_str = f"{start_h:02d}:{start_m:02d}:{start_s:06.3f}"
	            end_str = f"{end_h:02d}:{end_m:02d}:{end_s:06.3f}"
	
	            f.write(f"{start_str} --> {end_str}\n")
	            f.write(f"{segment.text.strip()}\n\n")
	
	    print(f"Finished & Saved: {vtt_path}")
	
	print("All audio files have been completely transcribed!")
	```

- In case you've interrupted the progress before - run this to resume with the progress
	- Install **setuptools** if you haven't already
		``` python
		pip install faster-whisper setuptools
		```
	- Create a python file for this script
		``` python
		import os
		import glob
		from faster_whisper import WhisperModel

		# 1. Initialize model using CPU (optimized via orientation CoreML/Accelerate on Mac)
		# Note: "mps" device is not natively supported by faster-whisper/ctranslate2 yet.
		model_size = "base"
		model = WhisperModel(model_size, device="cpu", compute_type="float32")
		
		# 2. Scan for all WAV files in the current directory
		wav_files = glob.glob("*.wav")
		
		for wav_path in wav_files:
		    # Generate the matching VTT filename
		    base_name = os.path.splitext(wav_path)[0]
		    vtt_path = f"{base_name}.vtt"
		
		    # Skip if the VTT file already exists
		    if os.path.exists(vtt_path):
		        print(f"Skipping: {vtt_path} already exists.")
		        continue
		
		    print(f"Processing: {wav_path}...")
		
		    # 3. Run transcription (forcing English language)
		    segments, info = model.transcribe(wav_path, language="en")
		
		    # 4. Write segments directly to a VTT formatted file
		    with open(vtt_path, "w", encoding="utf-8") as f:
		        f.write("WEBVTT\n\n")
		
		        for segment in segments:
		            # Format timestamps to HH:MM:SS.mmm
		            start_h, start_m, start_s = int(segment.start//3600), int((segment.start%3600)//60), segment.start%60
		            end_h, end_m, end_s = int(segment.end//3600), int((segment.end%3600)//60), segment.end%60
		
		            start_str = f"{start_h:02d}:{start_m:02d}:{start_s:06.3f}"
		            end_str = f"{end_h:02d}:{end_m:02d}:{end_s:06.3f}"
		
		            f.write(f"{start_str} --> {end_str}\n")
		            f.write(f"{segment.text.strip()}\n\n")
		
		    print(f"Saved: {vtt_path}")

		print("All files processed!")
		```

- Another option is this one-liner command
	``` python
python3 -c "import glob, os, faster_whisper; m=faster_whisper.WhisperModel('base', device='cpu', compute_type='float32'); [open(os.path.splitext(w)[0]+'.vtt','w',encoding='utf-8').write('WEBVTT\n\n'+''.join(f'{int(s.start//3600):02d}:{int((s.start%3600)//60):02d}:{s.start%60:06.3f} --> {int(s.end//3600):02d}:{int((s.end%3600)//60):02d}:{s.end%60:06.3f}\n{s.text.strip()}\n\n' for s in m.transcribe(w, language='en')[0])) for w in glob.glob('*.wav')]"
	```
**Step 3: Soft embed subtitle to video (mp4)**

	``` c
	for f in *.mp4; do ffmpeg -i "$f" -i "${f%.mp4}.vtt" -c copy -c:s mov_text "${f%.mp4}_subbed.mp4"; done
	```

	![[Pasted image 20260724173606.png|337]]

## QA
### Issue 1: Incompatible Video Codec
- Error
> [!ERROR] Error
> [mp4 @ 0x154e06e40] Could not find tag for codec vp8 in stream #0, codec not currently supported in container
> [out#0/mp4 @ 0x600003234240] Could not write header (incorrect codec parameters ?): Invalid argument
> [sost#0:2/mov_text @ 0x154e083b0] Task finished with error code: -22 (Invalid argument)
> [sost#0:2/mov_text @ 0x154e083b0] Terminating thread with return code -22 (Invalid argument)
> [out#0/mp4 @ 0x600003234240] Nothing was written into output file, because at least one of its streams received no packets.

- Solution: Re-encode video to H.264 (For valid MP4 output)
	``` shell
	for f in *.mp4; do
	  # Skip files that have already been subbed
	  [[ "$f" == *_subbed.mp4 ]] && continue
	  
	  ffmpeg -i "$f" -i "${f%.mp4}.vtt" -c:v libx264 -c:a copy -c:s mov_text "${f%.mp4}_subbed.mp4"
	done
	```

### Combining creating "subbed" folder and moving all subbed video into that folder
``` shell
mkdir -p subbed && for f in *.mp4; do ffmpeg -i "$f" -i "${f%.mp4}.vtt" -c copy -c:s mov_text "subbed/${f%.mp4}_subbed.mp4"; done
```
- **`mkdir -p subbed &&`**: This safely ensures the `subbed` directory exists before the loop starts so `ffmpeg` doesn't throw an error.
- **`"subbed/${f%.mp4}_subbed.mp4"`**: Changed the output path of `ffmpeg`. It now writes the subbed video straight into the target folder, saving you an extra disk write/move operation.

### Replace new soft embedded mp4 file with existing mp4 and vtt files
- Single file one-liner
	```shell
	ffmpeg -i video.mp4 -i video.vtt -c copy -c:s mov_text temp.mp4 && mv temp.mp4 video.mp4 && rm video.vtt
	```
- Multiple files
	```shell
	for video in *.mp4; do
	    base="${video%.mp4}"
	    if [ -f "$base.vtt" ]; then
	        ffmpeg -i "$video" -i "$base.vtt" -c copy -c:s mov_text "temp_$video" && \
	        mv "temp_$video" "$video" && \
	        rm "$base.vtt"
	    fi
	done
	```

### Extract vtt from mp4 file
``` shell
for file in *.mp4; do
    ffmpeg -i "$file" -map 0:s:0 "${file%.mp4}.vtt"
done
```
Note: Change that to a one-liner simply by adding `;`
``` shell
for file in *.mp4; do ffmpeg -i "$file" -map 0:s:0 "${file%.mp4}.vtt"; done
```

## Remove soft embedded subtitle
```shell
ffmpeg -i input.mp4 -vcodec copy -acodec copy -sn output.mp4
```
