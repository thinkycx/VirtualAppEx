# VirtualAppEx
VirtualApp 9.0适配\
仅供个人学习使用\
\
若您有其他用途，请去这里https://github.com/asLody/VirtualApp

# 修改部分说明

对于原先代码，结合需求，我做了如下的修改：

1. 使用sharedPreferences技术创建xml文件，记录安装次数，保证只安装一次。
2. 将asserts/下的apk文件复制到/data/data/<package.name>/files目录下。（asserts下的文件我无法获得绝对路径，因此只能复制到别的目录下来获取path）
3. 修改ListAppFragment的onViewCreated方法，指定apk的package name和path实现apk的安装。
4. 删除不需要的操作，如：askInstallGms。（检测google service）

# 备注

1. 原先安装apk时的调用链：ListAppActivity->ListAppFragement->onViewCreated->mInstallButton.setOnClickListener()->dataList.add()。
2. 原先的修改方式是在HomeActivity的initLaunchpad方法中调用dataList.add()。但是，只能实现安装apk，HomeActivity的View没有刷新，因此只能重新其中app才可以看见安装的apk。于是只好恢复add app这个button，在里面实现安装逻辑。
3. 如果需要安装新的apk，需要：1）复制apk到asserts/目录下 2）增加ListAppFragement中的dataList.add()方法，指定apk package name和复制之后的path即可。

2019.04.18 (spend about 5 days)
