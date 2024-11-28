
# 介绍


[JxAudio](https://github.com)是一个基于.net core的音频管理系统，支持音乐的播放、上传、下载、删除等功能。 兼容Subsonic协议，可以使用Subsonic客户端进行访问。 支持Windows、Linux、MacOS等操作系统。目前只提供Docker部署方式，其他方式须自行编译安装包，Windows和Linux提供ffmpeg二进制文件，MacOS需要自行安装ffmpeg。


# 特点


* 支持插件功能，可以自定义插件进行扩展
* 支持直连网盘，可以直接播放网盘音乐
* 目前官方支持Alist网盘直接播放
* 可自行扩展后台页面，对音乐进行自定义管理


# 优势


其最大的优势就是支持插件，可以利用插件直连网盘或者其他存储位置，目前已支持AList，可以通过AList扩展各种网盘。这样我们就可以将其安装在openwrt或者armbian上面，由于这些位置常常没有足够大的硬盘，无法作为存储位置，所以我们的常用音乐管理软件如Navidrome可能无法在上面安装。但是我们往往有一个比较大又用不到那么大的网盘，如阿里云盘或者OneDrive这种，我们完全可以将音乐放置在网盘上，然后通过AList挂载，然后使用JxAudio挂载AList网盘的形式直接播放阿里云盘或者OneDrive上的内容。这种方式由于是直接获取原生播放路径，所以不需要将AList通过WebDav或者其他方式模拟挂载为本地硬盘，相对而言效率会更高，并且出错的概率会更小。


 


同时，由于目前的AList和本地播放都是使用插件进行处理的，所以可以制作更多的插件，来满足更多的需求，比如直接挂载OneDrive，绕过AList，或者在线修改MusicTag，这都是可以做到的。


# 部署


目前JxAudio推荐通过Docker的方式进行部署，目前j4587698/jxaudio支持x64、arm64、armv7三种架构。




```
docker run -d -p 4587:4587 -v /path/to/config:/app/config -v /path/to/log:/app/log --name jxaudio j4587698/jxaudio
```



> 其中4587为程序默认监听端口。
> 
> 
> /app/config为配置文件所在目录，里面存放着安装配置以及歌曲封面的缓存，同时如果使用Sqlite作为数据库，则默认的数据库也会建立在这个目录下。
> 
> 
> /app/log是程序的日志目录。


同时JxAudio支持Windows、Linux、Macos，目前需要自行编译安装包，其中windows x86 x64，Linux x86 x64 armv7 arm64的ffmpeg已经内置，可以直接使用，macos或linux musl等系统或架构需要自行安装ffmpeg。


# 开源地址以及协议


目前项目使用GPL3\.0开源在Github：https://github.com/j4587698/JxAudio


欢迎大家star


# 客户端


目前官方客户端还在开发中，由于兼容Subsonic协议，所以目前可以使用"音流"作为客户端进行使用，服务器类型选择Subsonic即可。


 本博客参考[飞数机场](https://ze16.com)。转载请注明出处！
