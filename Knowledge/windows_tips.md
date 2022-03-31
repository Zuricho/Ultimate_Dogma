管理员模式 cmd

1) 按 Win+R 键打开”运行”功能，在窗口中输入 cmd 按 Ctrl+Shift+Enter 以管理员身份打开命令提示符，然后输入以下命令就可以禁用自带键盘：

```
sc config i8042prt start= disabled
```



2) 按 Win+R 键打开”运行”功能，在窗口中输入 cmd 按 Ctrl+Shift+Enter 以管理员身份打开命令提示符，然后输入以下命令就可以开启自带键盘：

```
sc config i8042prt start= auto
sc config i8042prt start= demand
```



