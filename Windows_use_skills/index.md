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

