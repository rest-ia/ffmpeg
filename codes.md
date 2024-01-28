#fps<br/>
ffmpeg -i video.mp4 -filter:v "setpts=PTS/1.5" -progress pipe:1 -stats -c:a copy out.mp4 -y
<br/>
<br/>
#x264 8b<br/>
ffmpeg -i %1 -map 0:0 -c:v libx264 -crf 23 -pix_fmt yuv420p -vf scale=1920:1080 %~n1y.mkv
<br/>
<br/>
<br/>
#divide<br/>
ffmpeg -i chi.mp4 -acodec copy -f segment -segment_time 30 -vcodec copy -map 0 stream%%05d.mp4
<br/><br/>
* ffmpeg -i a.mkv -map 0 -acodec copy -vcodec copy -ss 0 -t 1920.05 1.mkv
<br/><br/>
* ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 1920 -t 1920.05 2.mkv
<br/><br/>
ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 3800 -t 1920.05 3.mkv
