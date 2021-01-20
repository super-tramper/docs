##第一个shell脚本
&emsp;&emsp;打开文本编辑器，新建一个文件，扩展名为sh（sh代表shell），扩展名并不影响脚本执行，见名知意就好。  
输入代码如下：
  
	#!/bin/bash
	echo "Hello World!"
“#!” 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即使用哪一种Shell。echo命令用于向窗口输出文本。  
运行Shell脚本有两种方法。
###作为可执行程序
将上面的代码保存为test.sh，并 cd 到相应目录：  

	chmod +x ./test.sh  #使脚本具有执行权限
	./test.sh  #执行脚本
注意，一定要写成./test.sh，而不是test.sh。运行其它二进制的程序也一样，直接写test.sh，linux系统会去PATH里寻找有没有叫test.sh的，而只有/bin, /sbin, /usr/bin，/usr/sbin等在PATH里，你的当前目录通常不在PATH里，所以写成test.sh是会找不到命令的，要用./test.sh告诉系统说，就在当前目录找。  
###作为解释器参数
这种运行方式是，直接运行解释器，其参数就是shell脚本的文件名，如：  
	
	/bin/sh test.sh
	/bin/php test.php  
这种方式运行的脚本，不需要在第一行指定解释器信息，写了也没用。