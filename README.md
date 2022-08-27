# how to merge video and audio with fluent ffmpeg? 🤔
### Hello, I just found the answer to my big question, in this script I just show you what worked for me

✅ Using ffmpeg you need this command line (you have to have ffmpeg installed on your computer)
```
ffmpeg -i video.mp4 -i audio.wav -c:v copy -c:a aac output.mp4
```

✅ Using fluent-ffmpeg
```
// important dependencies
import ffmpegInstaller from '@ffmpeg-installer/ffmpeg';
import ffmpeg from 'fluent-ffmpeg';

// this script is necessary to not receive an error
ffmpeg.setFfmpegPath(ffmpegInstaller.path);

ffmpeg()
    .addInput(videoPath)
    .addInput(audioPath)
    .format('mp4')
    .saveToFile(`path to save/name of file`) // example ==> './temp/video.mp4'
    .on('error', err => console.log(err))
    .on('end', ()=> console.log('finish successfully'))
    on('progress', progress => console.log(progress))
```

### ✨With this code, you can combine the video and audio, but keep in mind that if you get the video and audio from a URL, they might save with errors.
