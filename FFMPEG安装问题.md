## FFmpeg安装问题

## 下载FFmpeg
```shell
git clone https://git.ffmpeg.org/ffmpeg.git
```

## 安装pkg-config
```shell
sudo apt-get install pkg-config
```

## 安装sdl2库(不然后面编译不出ffplay)
```shell
sudo apt-get install libsdl2-dev
```

## 编译FFmpeg
cd到FFmpeg的下载位置,笔者这里是~/Document/ffmpeg
```
cd ~/Document/ffmpeg
./configure --prefix=/usr/local/ffmpeg --enable-gpl --enable-nonfree --enable-libfdk-aac --enable-libx264 --enable-libx265 --enable-filter=delogo --enable-debug --disable-optimizations --enable-libspeex --enable-shared --enable-pthreads
```

不出意外应该会出现很多问题

### 缺少yasm
* 网上下载yasm安装包,这里笔者安装包名字为yasm-1.3.0.tar.gz
```shell
tar -zxvf yasm-1.3.0.tar.gz
cd yasm-1.3.0
./configure
sudo make && sudo make install
```

### 缺少libfdk_aac
```shell
sudo apt install libfdk-aac-dev
```

### 缺少speex
```shell
sudo apt install speex-devel
sudo apt-get install libspeex-dev
```

### 缺少libx264
```shell
sudo apt-get install libx264-dev
```

### 缺少libx265
```shell
sudo apt-get install libx265-dev
```

## 安装ffmpeg
```shell
sudo make && sudo make install
```

## 配置环境变量
打开~/.zsh_rc(或者~/.bash_profile,看你用的啥),添加:
```shell
export PATH=$PATH:/usr/local/ffmpeg/bin
export PKG_CONFIG_PATH=/usr/local/ffmpeg/lib/pkgconfig:$PKG_CONFIG_PATH
export LD_LIBRARY_PATH=/usr/local/ffmpeg/lib:$LD_LIBRARY_PATH
```
## 测试
```shell
ffmpeg
```
```shell
pkg-config --libs --cflags libavutil
```

没显示不好的信息就表示大功告成