ffmpeg-ios-compile
==================

Paid Tech Support Service
------------------

If you have trouble to compile the ffmpeg lib yourself, please mail to xiewei.max@gmail.com to get our paid service.
We have a modified compile environment for you to compile ffmpeg libs for iOS.


Free DIY
------------------

Those scripts help you compile ffmpeg libs for iOS Device/Simulator.
You need 'XCode Developer_3.2.5' to compile ffmpeg libs for iOS.

I compiled my own ffmpeg libs for iOS with the same scripts here without any errors.

Execute those shell scripts in root directory of ffmpeg v1.0.

1) config_i386.sh
Compile libs for iOS Simulator.

2) config_v6.sh config_v7.sh
Compile libs for armv6(iPhone 3G) / v7(iPhone 3Gs or later).

3) config_v7s.sh
Gcc 4.2 in Xcode does not support v7s.
This script is not working, have to upgrade.

4) config_x64.sh
Test ffmpeg on Mac.

5) combile_lipo.sh
Compbile specified arches into on universal lib file.

6) gas-preprocessor/
Before your run those scripts, copy gas-preprocessor.pl to your usr/bin.

7) armv7s/
Fake armv7s support


Usage example:

```shell
xw# cd ffmpeg-1.0

xw# make distclean
xw# ../config/config_v6.sh 
xw# make -j9 && make install

xw# make distclean
xw# ../config/config_v7.sh 
xw# make -j9 && make install

xw# make distclean
xw# ../config/config_vi386.sh 
xw# make -j9 && make install

xw# ../config/combile_lipo.sh

xw# open dist-universal
```


About Dolby
------------------

DO NOT use dolby tech in your iOS app unless you have a dolby license.

Those scripts have removed the following tech from your ffmpeg v1.0 configuration:

Dolby Digital (AC3)
Dolby Digital Plus (E-AC3)
Dolby TrueHD (MLP)


编译步骤
------------------
下面代码主要是解释原理的

```shell
echo -n "prepare to make ffmpeg with i386 ! "
   
cd ffmepg 
   
make distclean
   
../config/config_i386.sh
   
make -j9 && make install   

mv dist-i386  ../
   
echo -n "success make ffmpeg with i386 ! "
```

测试方法
------------------
测试

1.下载代码
```shell 
git clone https://github.com/i5ting/ffmpeg-ios-compile.git
cd ffmpeg-ios-compile
```

1.更新依赖子模块并编译
```shell 
ffmpeg-ios-compile git:(master) ✗ git submodule init
ffmpeg-ios-compile git:(master) ✗ git submodule update
ffmpeg-ios-compile git:(master) ✗ ./compile.sh 
```


