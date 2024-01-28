#fps
ffmpeg -i video.mp4 -filter:v "setpts=PTS/1.5" -progress pipe:1 -stats -c:a copy out.mp4 -y

#x264 8b
ffmpeg -i %1 -map 0:0 -c:v libx264 -crf 23 -pix_fmt yuv420p -vf scale=1920:1080 %~n1y.mkv
