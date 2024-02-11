#sharpen
ffmpeg -i /content/sp.mp4 -filter:v unsharp=5:5:1.0:5:5:0.0 -progress pipe:1 spb.mp4 -y

#fps<br/>
ffmpeg -i video.mp4 -filter:v "setpts=PTS/1.5" -progress pipe:1 -stats -c:a copy out.mp4 -y
<br/>
<br/>
#x264 8b
<br/>
ffmpeg -i %1 -map 0:0 -c:v libx264 -crf 23 -pix_fmt yuv420p -vf scale=1920:1080 %~n1y.mkv
<br/><br/>
#x264
<br/><br/>
ffmpeg -i %1 -map 0 -c:v libx264 -crf 22 -c:a copy %~n1y.mkv

<br/>
<br/>
<br/>
#divide<br/>
 ffmpeg -i chi.mp4 -acodec copy -f segment -segment_time 30 -vcodec copy -map 0 stream%%05d.mp4
<br/><br/>
 ffmpeg -i a.mkv -map 0 -acodec copy -vcodec copy -ss 0 -t 1920.05 1.mkv
<br/><br/>
 ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 1920 -t 1920.05 2.mkv
<br/><br/>
 ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 3800 -t 1920.05 3.mkv
<br/><br/>
 ffmpeg -i a.mkv -map 0 -acodec copy -vcodec copy -ss 0 -t 1920.05 1.mkv

 ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 1920 -t 1920.05 2.mkv

 ffmpeg -i a.mkv -map 0:0 -map 0:1 -map 0:2 -acodec copy -vcodec copy -ss 3800 -t 1920.05 3.mkv
<br/><br/>
Join
<br/>
ffmpeg -f concat -i videos.txt -c copy output.mp4
<br/><br/>
ffmpeg -i 1.mp4 -i 2.mp4 -i 3.mp4 -filter_complex "[0:v:0][0:a:0][1:v:0][1:a:0][2:v:0][2:a:0]concat=n=3:v=1:a=1[outv][outa]" output.mkv
<br/><br/>
Resolution
<br/>
ffmpeg -i a.mp4 -vf scale=640:360 -acodec copy b.mp4
<br/>
<br/>
#Audio MP3
<br/><br/>
ffmpeg -i d.mkv -vn -ar 44100 -ac 2 -b:a 320k  d22.mp3
<br/><br/>
ffmpeg -i video.mp4 -vn -ab 256000 audio.mp3
<br/><br/>
#Image to video
<br/><br/>
ffmpeg -r 1 -loop 1 -i ii.jpg -i a.mp3 -acodec copy -r 1 -shortest v.mp4
<br/>
Rotar 90° Izquierda
ffmpeg -i %1 -vf rotate=-90*PI/180 -c:a copy 90i.mp4
<br/><br/>
Rotar 90° Derecha
<br/><br/>
ffmpeg -i %1 -vf rotate=90*PI/180 -c:a copy 90d.mp4
