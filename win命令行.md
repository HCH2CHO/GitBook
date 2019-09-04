## Windows cmd

type nul>a.csv

cd.>a.csv

`more  文件名`   显示前几行

 copy 文件1/b +文件2/b +……+文件n/b   文件

dir  显示当前文件夹下文件

## PowerShell

`Get-Content file -TotalCount 2`    读取文件前2行

`Get-Command -Syntax  +文件  ` 	   同where

可使用基本的linux命令

```
ubuntu1804.exe config --default-user root
修改默认WSL用户
```

`powercfg /batteryreport` 生成电量情况



F2进入  bios

F12进入 boot manager

Boot Mode:UEFI

```
vim .bashrc
添加PS1='\[\e[32m\]\u@\h \W#\[\e[m\] '
source .bashrc
```

- 显示电量剩余时间

```
-转到搜索栏并键入注册表编辑器，然后选择以管理员身份运行
--导航到Hkey_LOCAL_MACHINE SYSTEM CurrentControlSet Control Power
--从右侧窗格中删除EnergyEstimationEnabled和UserBatteryDischargeEstimator
--右键单击并添加新DWORD（32位），并将其命名为EnergyEstimationDisabled
```



## 其他问题

- 两台电脑ping不通，**修改防火墙相关设置**。

  **步骤：**控制面板 →  系统和安全 → Windows防火墙 → 高级设置 → 入站规则 → 文件和打印机共享（回显请求 - ICMPv4-In）设置为启用。

- win总是提醒更换密码，设置密码长期有效：

  <https://www.windows10.pro/net-accounts-maxpwage-password-expiration/>

