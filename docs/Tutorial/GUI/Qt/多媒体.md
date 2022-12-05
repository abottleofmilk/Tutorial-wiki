## Qt多媒体
Qt多媒体模块提供了很多类，可以实现如下的一些功能：

访问原始音频设备进行输入或输出；低延迟播放音效文件，如WAV文件；使用播放列表播放压缩的音频和视频文件，如mp3、wmv等；录制声音并且压制文件；使用摄像头进行预览、拍照和视频录制；音频文件解码到内存进行处理；录制音频或视频时，访问其视频帧或音频缓冲区；数字广播调谐和收听。

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221204213319.png)

### 音频播放
QMediaPlayer可以播放经过压缩的音频或视频文件，如mp3、mp4、wmv等文件，QMediaPlayer可以播放单个文件，也可以和QMediaPlaylist类结合，对一个播放列表进行播放。

![](https://cdn.staticaly.com/gh/abottleofmilk/CDN@master/img/20221204214628.png)