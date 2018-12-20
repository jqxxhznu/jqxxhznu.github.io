
## DSAC的开源代码部署教程  2018.12.20 by 大豪
我的博客:https://blog.csdn.net/liu506039293


https://github.com/cvlab-dresden/DSAC


E. Brachmann, A. Krull, S. Nowozin, J. Shotton, F. Michel, S. Gumhold, C. Rother,
"DSAC – Differentiable RANSAC for Camera Localization",CVPR 2017


## 关于这篇论文
这篇论文是关于深度学习用于相机姿态估计上的。网上资料比较少，花了3天跑了下代码。遇到了不少坑，来填一下，方便后来人查看。因为写这篇教程的时候时间有点久远了，记忆有点不清晰，请后来的学弟运行完后补充。我的基本运行环境是Ubuntu16.04+cuda9.0（推荐cuda8.0）
## 安装的环境
1. OpenCV 2.4
opencv在ubuntu中的安装非常的麻烦，推荐使用别人写好的脚本。
https://github.com/jayrambhia/Install-OpenCV
然后运行下面的代码
> sudo chmod +x *.sh
> sudo sh ./opencv2_4_10.sh

    装这个时间会比较久一点，有一两个错误不影响最后的结果
2. PNG++
由于PNG++是基于libpng-1.2.x的版本，所以这里我们下载1.2.53版本 
下载地址： 
http://sourceforge.net/projects/libpng/files/libpng12/1.2.53/libpng-1.2.53.tar.xz/download 
>./configure
make check
sudo make install
make check
sudo ldconfig


3.  cuDNN
这个程序要求cuDNN的版本是5（忘了是torch还是lua的要求了，学弟补一下），我的cuda9对应的是7，但是我用5版本的替换发现也成功了。

4. 安装GCC 4.8.4，这个版本不严格

5. 安装lua5.3，没遇到什么问题，按官网来就行。之前用7版本一直不行，换了5.3版本就行了，可能是有版本问题，最好用5.3。

6. 安装torch
安装Torch7比较简单，按照http://torch.ch/docs/getting-started.html 上的步骤安装即可。
输入th，出现torch7标志即可。

## 部署程序
1. git上把代码down下来 
https://github.com/cvlab-dresden/DSAC
2.  目录结构
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181220205158799.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdTUwNjAzOTI5Mw==,size_16,color_FFFFFF,t_70)
3.下载几个文件
https://www.microsoft.com/en-us/research/project/rgb-d-dataset-7-scenes/ 
把权重和网络放到对应位置
4.运行下面的命令就行了
>cd core
mkdir build
cd build
cmake ..
make

5.验证成功，以棋盘项目为例
![在这里插入图片描述](https://img-blog.csdnimg.cn/2018122020593766.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdTUwNjAzOTI5Mw==,size_16,color_FFFFFF,t_70)

