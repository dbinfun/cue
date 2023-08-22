最近有个需求,需要在`Ubuntu22.04`中安装`VirtualBox`，安装没有什么问题,但是安装后遇到了VirtualBox无法创建网卡,在网上查找了下相关问题,在此记录。

<!-- more -->

## 安装VirtualBox

甲骨文官网下载Linux版本安装即可[Oracle VM VirtualBox - Downloads](https://www.oracle.com/cn/virtualization/technologies/vm/downloads/virtualbox-downloads.html) 目前最新的版本是7.0

```sh
sudo dpkg -i virtualbox-7.0_7.0.10-158379~Ubuntu~jammy_amd64.deb
```

在安装时会遇到`Securty Boot`相关的选项,输入一次性密码后重启,重启后可以根据提示直接选择签名,我选择的直接reboot,导致无法使用网卡。

## 解决无法使用网卡

根据这个[issues](https://github.com/gasolin/foxbox/issues/32) 运行`sudo modprobe vboxnetadp` 发现报错如下

```txt
modprobe: ERROR: could not insert 'vboxnetadp': Key was rejected by service
```

根据这篇文章解决：https://blog.csdn.net/hydront/article/details/130280075

以下内容来自 https://blog.csdn.net/hydront/article/details/130280075

---

我选择的是解决方式B（不关闭secure boot validdation）

1、确定安装了mokuli 和shim-signed

```sh
sudo apt install mokutil
sudo apt install shim-signed
sudo update-secureboot-policy --new-key
```

2创建签名密钥

直接输下面代码。该命令会在`/var/lib/shim-signed/mok/`下生成证书(MOK.der)和私钥(MOK.priv)

```sh
openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=Descriptive common name/"
```

注意：为了获更安全，可以将-nodes去掉，然后它会要求输入密码。在继续下一步之前，输入：export KBUILD_SIGN_PIN='yourpassword'。之前没有去掉-nodes的可以把生成的MOK.der和MOK.priv删了，重新输一遍代码。

3对模块签名

本例为vboxnetadp，对其他模块可以通过修改最后边的ls $dirname（modinfo-n vboxnetadp））/vbox*.ko）以获得完整功能。（针对不同问题的可以根据实际情况来试下修改最后的der $(modinfo -n vboxnetadp））

```sh
cd /var/lib/shim-signed/mok/
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vboxnetadp)
```

4确认模块已签名

```sh
tail $(modinfo -n vboxnetadp) | grep "Module signature appended"
```

5注册密钥

重要！它会要求你输入密码，输入的密码是只需要在下次重新启动时使用的一次性密码。

```sh
sudo mokutil --import MOK.der
```

6重启并按照说明注册MOK

7检查输入以下代码来确认密钥已注册

```sh
mokutil --test-key MOK.der
```

使用该方法的话每次内核更新都需要重新注册下密钥。

## 最后

重启后就可以运行Virtualbox正常创建网卡了,如果不行再运行一次`sudo modprobe vboxnetadp`