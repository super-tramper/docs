##如何进入Shell
&emsp;&emsp;在 Linux 发展的早期，唯一能用的工具就是 Shell，Linux 用户都是在 Shell 中输入文本命令，并查看文本输出；如果有必要的话，Shell 也能显示一些基本的图形。

&emsp;&emsp;而如今 Linux 的环境已经完全不同，几乎所有的 Linux 发行版都使用某种图形桌面环境（例如 GNOME、KDE、Unity 等），这使得原生的 Shell 入口被隐藏了，进入 Shell 仿佛变得困难起来。  
###进入Linux控制台
&emsp;&emsp;一种进入 Shell 的方法是让 Linux 系统退出图形界面模式，进入控制台模式，这样一来，显示器上只有一个简单的带着白色文字的“黑屏”，就像图形界面出现之前的样子。这种模式称为 Linux 控制台（Console）。

&emsp;&emsp;现代 Linux 系统在启动时会自动创建几个虚拟控制台（Virtual Console），其中一个供图形桌面程序使用，其他的保留原生控制台的样子。虚拟控制台其实就是 Linux 系统内存中运行的虚拟终端（Virtual Terminal）。

&emsp;&emsp;从图形界面模式进入控制台模式也很简单，往往按下Ctrl + Alt + Fn(n=1,2,3,4,5...)快捷键就能够来回切换。

&emsp;&emsp;例如，CentOS 在启动时会创建 6 个虚拟控制台，按下快捷键Ctrl + Alt + Fn(n=2,3,4,5,6)可以从图形界面模式切换到控制台模式，按下Ctrl + Alt + F1可以从控制台模式再切换回图形界面模式。可以发现，1号控制台被图形桌面程序占用了。  
###使用终端
&emsp;&emsp;进入 Shell 的另外一种方法是使用 Linux 桌面环境中的终端模拟包（Terminal emulation package），也就是我们常说的终端（Terminal），这样在图形桌面中就可以使用 Shell。
