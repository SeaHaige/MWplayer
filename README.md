Mwplayer的一些主要特点和功能：

基于C++开发，使用中间件技术开发，支持HTML5网页播放视频，调用简单，CPU占用率低。
支持多种协议(RTSP/RTMP/HLS/HTTP-FLV/MP4)的视频点播和直播，支持H265视频解码。
支持画面秒开、极低延时。 提供完善的Javascript API,也可以作SDK用，供其他语言调用。
全面支持H265/H264/AAC/G711。
Mwplayer是一个功能强大且高性能的中间件播放器，适用于构建实时音视频传输和处理的网页应用，如直播、视频会议、视频监控等。它提供了多种流媒体协议的支持，具有低延迟和分屏播放能力。 

使用环境
因为Mwplayer是基于C++开发的一款用于网页播放视频的插件，所以支持javascript的网页环境都可以使用(目前支持windows平台运行)。

安装说明

Mwplayer使用中间件方式播放视频文件，需要上传js文件和安装包至网站目录里即可使用，js调用时候会自动提示用户下载安装插件。检测播放插件安装代码


let player=new mwplayer();
player.checkplugin(function(result){
        if(result){
                ...
                //插件安装成功
        }else{
                ...
                //未检测到插件
        }
});

调用方式

var videoObject = {
        container: '.video',//“#”代表容器的ID，“.”或“”代表容器的class
        download:'mwplayer.exe',//插件安装文件下载地址，需要复制安装文件至网页服务器
        title:'video',               //设定播放器标题
        video:'http://***'        //视频地址支持httpFlv,HLS,rtsp等视频传输协议
 };

        

 定义播放器初始化时的各种设置

new mwplayer(videoObject);

播放器操作

player.hide()                       //隐藏视频播放

player.show()                     //显示视频播放

player.layout()                     //重新定位播放器位置

mwplayer.setHTMLTemplate(id,html) 
//设置播放模板HTML,id可以为"connect" "end" "retry" "fail" "retrying"

player.destroy()                     //结束视频播放



视频截图

player.snap(function(blob){
            const url = window.URL.createObjectURL(blob);
            // 创建链接
            const link = document.createElement("a");
            link.href = url;
            link.download = "test.jpg";
            // 模拟点击链接进行下载
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            // 释放 URL 对象
            window.URL.revokeObjectURL(url);
        })



