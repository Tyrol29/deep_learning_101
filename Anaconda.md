[TOC]

## 一、安装NVIDIA显卡驱动

去英伟达的官网下载驱动，找到自己对应的型号搜索驱动：[英伟达官网驱动下载](https://www.nvidia.cn/download/index.aspx?lang=cn)，如果是笔记本的话注意选Notebooks版本的。

![image-20240508095907417](.\imgs\image-20240508095907417.png)

以本文使用的Nvidia GeForce GTX1650为例

![image-20240508100450005](.\imgs\image-20240508100450005.png)

搜索出之后点击下载，执行默认安装即可。

安装完成后运行以下代码：

```
nvidia-smi
```

![微信图片_20240508094714](.\imgs\image_20240508094714.png)

如果可以出现以上输出结果，则说明你的电脑已正常安装Nvidia驱动，并非说明已安装cuda。此处的CUDA Version为当前驱动版本支持的最高CUDA版本。

## 二、安装CUDA

1.下载CUDA

去[英伟达开发者网站](https://developer.nvidia.com/cuda-toolkit-archive)下载CUDA，根据上面步骤显示的最高版本，选择合适的版本。这里我以11.3为例。

注意：显卡驱动尽量安装最新的，CUDA不是越新越好。一般要根据显卡型号/所跑的网络要求的pytorch环境等来安装。

![image-20240508101309997](.\imgs\image-20240508101309997.png)

依次点选下面几项，即可开始下载。

![image-20240508101446072](.\imgs\image-20240508101446072.png)

下载完成后执行默认安装即可。

2.验证安装

在命令行中输入

```
nvcc -V
```

![image-20240508095332495](.\imgs\image-20240508095332495.png)

出现以上结果表示CUDA已被安装，当前使用的CUDA版本为11.3

3.配置环境变量

如果上述命令无法正确输出，则是没有自动配置好环境变量，请重启再次输入上述命令。

若重启仍无法解决，则需要手动配置环境变量。

此电脑（右键）->属性->高级系统设置->环境变量，点击Path->编辑->新建，分别输入CUDA安装目录下\lib\x64的路径。

CUDA默认安装在C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3

将以下路径添加到环境变量：

```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3\lib\x64
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3\bin
```

最后确定保存。重启再次运行

```
nvcc -V
```

来验证。

## 三、安装cuDNN

1.去[cuDNN的官网]([cuDNN Archive | NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-archive))下载cuDNN文件，这个稍微麻烦些，需要注册英伟达的开发者账号才能下载，不知道咋注册就baidu一下注册步骤吧。一定要注意，cuDNN的版本和CUDA的版本是需要对应的，不然不能用。

![image-20240508102203996](.\imgs\image-20240508102203996.png)

选择和你安装的CUDA版本对应的cuDNN。

![image-20240508102342949](.\imgs\image-20240508102342949.png)

选择Windows版本的。

2.下载完是一个压缩包，解压后文件目录如下：

![image-20240508102819645](.\imgs\image-20240508102819645.png)

3.进入CUDA的安装目录：如果是默认安装的话是：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3，如果你修改过CUDA的安装目录，可以在系统的环境变量里找到安装位置：

![image-20240508103150703](.\imgs\image-20240508103150703.png)

4.把下载的cuDNN里bin、lib、include文件夹里面的内容复制到安装目录下的bin、lib、include目录下面，注意是文件夹里面的内容，不是复制整个文件夹。

![image-20240508103330112](.\imgs\image-20240508103330112.png)

## 四、Anaconda3安装

1.去[官网下载](https://www.anaconda.com/products/individual#Downloads)Anaconda3，输入邮箱会自动将下载连接发送到你的邮箱。

![image-20240508104431035](.\imgs\image-20240508104431035.png)



或者使用网盘下载：

链接：https://pan.baidu.com/s/1DnM5C9AvyfA0CwPzOZtzKg 
提取码：ro3f

2.安装，选择自己的安装目录，一路点击next。

![image-20240508105115553](.\imgs\image-20240508105115553.png)

3.安装完后，命令行执行`conda --version`，输出如下则安装成功：

![image-20240508105749873](.\imgs\image-20240508105749873.png)

4.如果没有成功，重启一下电脑再试一下，还是不行的话就手动添加环境变量：先找到Anaconda3的安装目录，把这3个路径加入Path环境变量，步骤如同上面CUDA添加环境变量：

![image-20240508105842339](.\imgs\image-20240508105842339.png)

注意要改成你的安装位置。

5.再执行一下命令，可以了。现在可以使用conda来创建虚拟环境了。

