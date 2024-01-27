ffmpeg -i video.mp4 -filter:v "setpts=PTS/1.5" -progress pipe:1 -stats -c:a copy out.mp4 -y
