# Gaussain09 基于linux的安装
- by 刘高勇
- liugaoyong_88@163.com
- 软件官网：http://gaussian.com/
-------

## **需要的东西：** ##
 - G09安装包
 - linux环境


## **安装步骤：** ##
1. 解压安装包
```sh
tar -zxcf g09.tar.gz
```
2. 把g09移动到某文件夹下（比如， /usr/local）
```sh
mv g09 /usr/local
```
3. 新建`screch`文件夹
```sh
mkdir /home/当前用户名/scr
```

4. 将下列内容加到==本用户==的`.bashrc`文件尾部
   （注：冒号一定要有！！！）
```sh
# Gaussian 09 setup
g09root="09的父目录"
export g09root
GAUSS_EXEDIR="09的父目录/g09"
export GAUSS_EXEDIR
GAUSS_SCRDIR="/home/当前用户名/scr"
export GAUSS_SCRDIR
. $g09root/g09/bsd/g09.profile
```


----
##  注：关于如何启用其他用户使用g09
- 重复上面的 3 和 4 步骤
- 添加本用户到`g09`所属用户组：`gpasswd -a 用户名 组名`
