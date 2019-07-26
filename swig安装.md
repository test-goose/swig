1、下载swig2.0.9版本，地址：http://www.swig.org/download.html

2、安装gcc、g++(已有则跳过此步)

\#yum -y install gcc automake autoconf libtool make

\#yum install gcc gcc-c++

3、安装PCRE，地址：Perl Compatible Regular Expressions Perl Compatible Regular Expressions Perl Compatible Regular Expressions Perl Compatible Regular Expressions（已有则跳过）

\#./configure

\#make && make install

4、解压swig2.0.9并编译安装

\#./configure --prefix=/usr/local/swig2.0.9

\#make && make install

5、安装完成后将路径添加到文件，#vim /etc/profile ，在最后添加一行：PATH=/usr/local/swig2.0.9/bin:PATH。保存后重新加载生效：PATH。保存后重新加载生效：*P**A**T**H*。保存后重新加载生效：source /etc/profile

6、尝试运行swig，如果出现swig:error while loading shared libraries:libpcre.so.1异常，则运行#ldd $(which swig)，理论上会看到libpcre.so.1 => not found。

7、手动添加链接：#ln -s /usr/local/lib/libpcre.so.1 /lib，完毕后再次运行swig，一切正常，#swig -version可看到版本

如果出现以下错误，解决方法如下
![如果出现](https://img-blog.csdnimg.cn/20190603165225864.jpg)
方法一、

1、打开 vi /etc/sysconfig/network-scripts/ifcfg-eth0（每个机子都可能不一样，但格式会是“ifcfg-eth数字”），把ONBOOT=no，改为ONBOOT=yes

2、重启网络：service network restart

方法二、

1、打开 vi /etc/resolv.conf，增加 nameserver 8.8.8.8

2、重启网络: service network restart