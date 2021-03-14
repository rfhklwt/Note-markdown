# Deepin 20.1 安装CUDA11

## 准备工作
1. `CUDA`的`runfile`[安装包](https://developer.nvidia.com/cuda-downloads)，下载后名字类似`cuda_11.1.0_455.23.05_linux.run`，中间代表版本号，请把它下载到`~/Downloads`文件夹这里。
2. 如果你使用的是`zsh`，请切换到`bash`，避免`bug`

### 第一步：禁用系统默认驱动
```shell
$ sudo vim /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
```
添加以下内容，这里也可以使用粘贴：
```
blacklist nouveau
options nouveau modeset=0
```
完了后按`ese`并输入`:wq`然后`Enter`保存

### 第二步：更改启动配置
```shell
$ sudo cp /boot/initrd.img-$(uname -r){,.with_nouveau}
$ sudo update-initramfs -u
```
### 第三步：卸载`Nvidia`等相关驱动和软件（没错，就是卸载，不要怀疑）
```shell
$ sudo apt purge nvidia-*
$ sudo reboot
```

## 安装`CUDA`里面自带的驱动
**注意**：后面会用`tty2`的终端，无法复制，因此建议你把这个`markdown`，放到`ipad`上边看边输入。

电脑重启后，如果发现电脑卡在启动界面，不要慌张（也可能不会卡在启动界面），anyway，此时按`Ctrl + Alt + F2`进入`tty2终端`。

**注意**：如果你使用的是`zsh`，请切换到`bash`，避免`bug`
```shell
$ sudo service lightdm stop
$ cd ~/Downloads
$ sudo ./cuda_11.1.0_455.23.05_linux.run --silent --driver # 注意这里的runfile文件名字得更改为你自己的
$ sudo reboot
```
这样子我们的驱动就装好了，正常的话就可以进入桌面了

## 安装`CUDA`
1. 首先按`Ctrl + Alt + F2`进入`tty2终端`，然后输入(记得是在`bash shell`下)：
```shell
$ sudo service lightdm stop
$ cd ~/Downloads
$ sudo ./cuda_11.1.0_455.23.05_linux.run --silent --toolkit --samples --librarypath=/usr/local/cuda
# 注意，上面这行命令安装CUDA，注意执行后是否显示失败failed
$ sudo service lightdm start
```

2. 这时会启动桌面，接下来需要测试`CUDA`安装是否成功，打开终端，依次执行以下命令：
```shell
$ cd ~/NVIDIA_CUDA-11.1_Samples/1_Utilities/deviceQuery # 注意这里的NVIDIA文件夹的名字根据你下载的CUDA的版本号不同而有所不同
$ make
$ ./deviceQuery
```
**如果最后显示`Result = pass`，说明安装成功了。**

## 写入配置文件
如果你用`bash`，就写入到`~/.bashrc`，如果你用`zsh`，就写入到`~/.zshrc`。（两个都写进去也`ok`）
```shell
$ vim ~/.zshrc
```
或者
```shell
$ vim ~/.bashrc
```
然后把如下路径复制到最后一行：
```
CUDA_HOME=/usr/local/cuda
export PATH=$PATH:$CUDA_HOME/bin/
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CUDA_HOME/lib64
```
完了后按`ese`并输入`:wq`然后`Enter`保存。接着在终端里面输入：
1. 如果是`zsh`
```shell
source ~/.zshrc
```
2. 如果是`bash`
```shell
source ~/.bashrc
```


