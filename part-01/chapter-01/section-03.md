# 安装Symfony2 #

## 获取Symfony2 ##

有好几种方式可以安装Symfony2：直接下载zip包安装，通过Composer安装，通过Symfony Installer来安装。这里我们用Symfony Installer来安装，这也是目前官方唯一推荐的方式。这个Symfony Installer其实是个PHP程序，你需要先把它安装到你的操作系统里，而且要求你的PHP版本至少是5.4；如果你的PHP版本不够，那就只能用其它两种方式下载安装了。

先安装Symfony Installer到操作系统中，并使它有执行权限。
```shell
$ sudo curl -LsS http://symfony.com/installer -o /usr/local/bin/symfony
$ sudo chmod a+x /usr/local/bin/symfony
```
用Symfony Installer来建立一个新项目，这个新项目就放在/var/www/Symfony目录下
```shell
$ cd /var/www
$ symfony new Symfony
```
