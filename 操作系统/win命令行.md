win+R 运行

Ctrl + L 快速把输入焦点转移到地址栏

地址栏输入wt 、cmd、powershell可在当前目录打开

> 修改了配置文件中的"startingDirectory":"."  ，但会导致直接点开wt会走到exe所在目录而不是用户目录下

## Windows cmd

type nul>a.csv

cd.>a.csv

`more  文件名`   显示前几行

 copy 文件1/b +文件2/b +……+文件n/b   文件

dir  显示当前文件夹下文件

```bash
#定位到文件
./test.sh  > log.txt 2>&1
```

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
#设置为绿色
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

