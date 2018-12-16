### 0x01
```bash
export EDITOR=vi #将vi添加到环境变量里面（当前用户）
```
### 0x02
```bash
apt edit-sources #编辑 软件包源 文件
```
### 0x03
<kbd>音量上+q</kbd> #调出termux软键盘
### 0x04
按键盘上<kbd>i</kbd>插入
```bash
deb [arch=all, aarch64]https://mirrors.tuna.tsinghua.edu.cn/termux stable main
```
按<kbd>i</kbd>表示从只读模式切换成编辑模式，**aarch64** 表示 **arm64** 位架构，**arm** 表示 **arm32** 架构，**i386** **intel 32位** 架构，**x86_64** **intel 64位** 架构

### 0x05
按<kbd>ESC</kbd>键退出编辑模式#退出编辑模式回到只读模式
### 0x06
按<kbd>Shift+:</kbd>再<kbd>w+q</kbd> 保存退出#在只读模式下按 <kbd>Shift</kbd>: 进入到操作模式，<kbd>w</kbd>:表示保存 （write），<kbd>q</kbd>:表示提出（quit），<kbd>wq!</kbd>:表示保存退出,<kbd>q!</kbd>:表示不保存，<kbd>!</kbd>:表示强制
### 0x07
```bash
pkg update  #更新包（更新系统）
```
### 0x08
```bash
pkg install hollywood cmatrix #安装cmatrix软件包
```
### 0x09
```bash
cmatrix #运行cmatrix ，不想继续运行就按ctrl+c 终止进程
```
### 0x10
根据自己需要装想装的工具
