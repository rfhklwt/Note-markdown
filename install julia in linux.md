## Installation
* Open a new terminal and go to your Downloads folder:
```shell
$ cd ~/Downloads
```
* Use `wget` to retrieve the latest compressed `Julia Linux Binaries`: 
(For more information, see help in [link](https://julialang.org/downloads/)
```shell
$ wget https://julialang-s3.julialang.org/bin/linux/x64/1.5/julia-1.5.3-linux-x86_64.tar.gz
```
* Extract the `.tar.gz`:
```shell
$ tar zxvf julia-1.5.3-linux-x86_64.tar.gz
```
* Copy the extracted folder to `/opt`:
```shell
$ sudo cp -r julia-1.5.3 /opt/
```
* Finally, create a symbolic link to `julia` inside the `/usr/local/bin `folder:
```shell
$ sudo ln -s /opt/julia-1.5.3/bin/julia /usr/local/bin/julia
```