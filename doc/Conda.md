# Conda

[TOC]

<details>
<summary>资料参考</summary>

[Anaconda-用conda创建python虚拟环境 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/94744929)

</details><br>


- **conda 简介**

conda可以理解为一个工具，也是一个可执行命令，其核心功能是包管理和环境管理。包管理与pip的使用方法类似，环境管理则是允许用户方便滴安装不同版本的python环境并在不同环境之间快速地切换。

- **conda的设计理念**

conda将几乎所有的工具、第三方包都当作package进行管理，甚至包括python 和conda自身。Anaconda是一个打包的集合，里面预装好了conda、某个版本的python、各种packages等。

**安装Anaconda：**打开命令行输入conda -V检验是否安装及当前conda的版本。

### Conda 操作

- **检查更新**

`conda update conda`

### 虚拟环境操作

- **查看现有虚拟环境**

`conda env list 
conda info -e`

- **创建虚拟环境**

`conda create -n your_env_name python=x.x`

anaconda命令创建python版本为x.x，名字为your_env_name的虚拟环境。**your_env_name**文件可以在Anaconda安装目录envs文件下找到。

- **激活或者切换虚拟环境**

打开命令行，输入python --version检查当前 python 版本。

`Linux:  source activate your_env_nam
Windows: activate your_env_name`

- **关闭虚拟环境**（即从当前环境退出返回使用PATH环境中的默认python版本）

`deactivate env_name`
或者``activate root``切回root环境
``Linux下：`source deactivate`

- **删除虚拟环境**

`conda remove -n your_env_name --all`

## 包操作

- **查看现有包**

`conda list`

- **在虚拟环境中安装额外的包**

`conda install -n your_env_name [package]`

- **删除虚拟环境中的某个包**

`conda remove --name $your_env_name  $package_name`

### 镜像设置

[Anaconda](http://anaconda.org/) 的服务器在国外，安装多个packages 时，conda下载的速度经常很慢。这时候把国内镜像例如：含有 Anaconda 仓库镜像的清华 TUNA 镜像源加入conda的配置即可：

- **添加含有 Anaconda 仓库镜像的 TUNA 的镜像**

`conda config --add channels [https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/](https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/)`

注意：TUNA 的 help 中镜像地址加有引号，需要去掉

- **设置搜索时显示通道地址**

`conda config --set show_channel_urls yes`

- **恢复默认镜像**

`conda config --remove-key channels`





Linux 安装 miniconda

```bash
linux 中安装miniconda
1、下载最新版 miniconda：

wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
2、在bash中安装：

sh Miniconda3-latest-Linux-x86_64.sh
3、安装完成后，关闭terminal后，重新打开，输入以下命令以验证是否安装成功：

conda -V
4、若要卸载，可直接删除已安装的文件夹后，并删除相应的环境变量：

rm -rf /usr/local/miniconda/
rm -rf /usr/local/anaconda/
删除后，打开 ~/.bashrc 文件，删除以下conda的路径变量：

export PATH=" /usr/local/anaconda/bin:$PATH" 
export PATH=" /usr/local/miniconda3/bin:$PATH" 
参考资料
install-miniconda-on-centos-7-redhat-7


```

jupyter

```bash
# 配置
jupyter-notebook --generate-config --allow-root

#非后台运行:
jupyter notebook --ip=0.0.0.0 --port=8080 --no-browser --allow-root
#后台运行:
nohup jupyter notebook --ip=0.0.0.0 --port=8080 --no-browser --allow-root > test.log 2>&1 &
```

可以通过配置`auto_activate_base`关闭自动进入[conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020)基础环境：
`conda config --set auto_activate_base false`
如要开启，将其设为`true`就可以了：
`conda config --set auto_activate_base true`

另：
可通过`conda config -h`查看帮助信息，通过`conda config --show`查看全部配置。





## 1.3.启用jupyter notebook的插件

**以下操作在终端内执行**

**1）下载两个插件包：**

- pip install jupyter_contrib_nbextensions -i https://pypi.tuna.tsinghua.edu.cn/simple
- pip install jupyter_nbextensions_configurator -i https://pypi.tuna.tsinghua.edu.cn/simple

**2）对插件进行设置：**

- jupyter contrib nbextension install --user
- jupyter nbextensions_configurator enable --user

记得设置完插件后要重启jupyter





juoyter环境文找到

```bash
在这个环境中依次输入如下命令

conda install ipykernel
conda install nb_conda

conda install ipykernel && conda install nb_conda
然后再输入：

jupyter notebook
```

