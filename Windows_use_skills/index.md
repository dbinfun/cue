## 使用技巧

## 问题解决

### 端口占用

在使用clash 的TUN模式的时候总是遇到端口为0的情况,就是应为端口占用,windows端的端口占用解决方法和linux端有些不一样.

打开powershell

查询被占用的端口 如7890

```powershell
netstat -ano | findstr 7890
```

会输出类似以下内容:

```txt
 TCP    0.0.0.0:7890           0.0.0.0:0              LISTENING       11872
```

通过id可以查看详细信息

```powershell
tasklist | findstr "11872"
```

终止进程就可以解除占用(需要管理员权限)

```powershell
 taskkill /pid 11872 /f
```

## 我的常用软件

**广告弹窗拦截**：[火绒安全](https://www.huorong.cn/) (广告拦截只是其众多功能的一个)

**注册表清理**：[CCleaner](https://www.ccleaner.com/) (清理注册表只是其众多功能的一个,部分付费)

**卸载工具**：[Uninstall Tool](https://crystalidea.com/uninstall-tool)

**压缩解压**：[Bandizip](https://www.bandisoft.com/bandizip/) (有广告但是不多)，[7-Zip](https://www.7-zip.org/)

**视频播放**：[PotPlayer](http://www.potplayercn.com/)

**浏览器**：[Microsoft Edge](https://www.microsoft.com/zh-cn/edge/download)，[Google Chrome](https://www.google.com/chrome/)，[Fire fox](https://www.mozilla.org/zh-CN/firefox/new/) (`国际原版`网站是没有备案号的)，[Tor](https://blog.torproject.org/) 

**下载工具**：[Internet Download Manager(IDM)](https://www.internetdownloadmanager.com/)，[迅雷](https://dl.xunlei.com/)(虽然饱受诟病，但是自带科学上网)

**网络工具**：[clash_for_windows](https://github.com/Fndroid/clash_for_windows_pkg)，[v2rayN](https://github.com/2dust/v2rayN)，[SocksCap64](https://www.sockscap64.com/homepage/)(这玩意儿很久没更新了,在某些情况下会有用)

**文件搜索**：[Everything](https://www.voidtools.com/zh-cn/) (由于个人分类管理文件比较勤快,所以基本不用)

**远程协助**：[向日葵](https://sunlogin.oray.com/)

**密码管理**：[KeePass Password](https://keepass.info/) (自定义云端同步密码，在主密钥未泄漏的情况下保证密码安全,安卓端:[keepass2android](https://github.com/PhilippC/keepass2android))，[Microsoft Edge](https://www.microsoft.com/zh-cn/edge/download)，[Google Chrome](https://www.google.com/chrome/)

**文本编辑**：[notepad--](https://gitee.com/cxasm/notepad--)(不用notepad++，不为什么)，[Typora](https://typora.io/)(主要用于写markdown)，[Visual Studio Code](https://code.visualstudio.com/)(只用来做文本编辑器大材小用了)  (优秀的文本编辑器实在太多了不一一例举了)

**快捷工具**：[uTools](https://u.tools/)(部分付费)，[Quicker](https://getquicker.net/)

**跨设备键鼠**：[Synergy](https://symless.com/synergy)(付费)

**虚拟机**：[Oracle VM VirtualBox](https://www.virtualbox.org/)，[Workstation Pro](https://www.vmware.com/cn/products/workstation-pro.html)(付费)

**磁盘分析工具**：[磁盘分析工具](http://www.uderzo.it/main_products/space_sniffer/index.html)

**其他**：[图吧工具箱](http://www.tbtool.cn/)(包含各类硬件工具)

---

有关开发的工具(仅是个人需要)：

**开发工具**：[JetBrains 全家桶](https://www.jetbrains.com/)(部分付费)，[Visual Studio Code](https://code.visualstudio.com/)，[Visual Studio](https://visualstudio.microsoft.com/zh-hans/vs/)，

**接口测试**：[Apifox](https://apifox.com/)，[Postman](https://www.postman.com/)(付费)，[Apipost](https://www.apipost.cn/)

**数据库工具**：[Navicat](https://navicat.com.cn/)(付费)

**Git可视化**：[Sourcetree](https://www.sourcetreeapp.com/)

**抓包工具**：[Wireshark](https://www.wireshark.org/)，[Fiddler](https://www.telerik.com/fiddler)

**SSH工具(终端)**：[MobaXterm](https://mobaxterm.mobatek.net/)(部分付费)，[Bitvise](https://www.bitvise.com/)，[FinalShell](http://www.hostbuf.com/)(打包上传比较方便,但收费)

