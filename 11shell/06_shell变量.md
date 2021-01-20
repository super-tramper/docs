##Shell变量：Shell变量的定义、删除变量、只读变量、变量类型
变量是任何一种编程语言都必不可少的组成部分，变量用来存放各种数据。脚本语言在定义变量时通常不需要指明类型，直接赋值就可以，Shell 变量也遵循这个规则。  
在 Bash shell 中，每一个变量的值都是字符串，无论你给变量赋值时有没有使用引号，值都会以字符串的形式存储。  
###定义变量
Shell 支持以下三种定义变量的方式：  

	variable=value
	variable='value'
	variable="value"
variable 是变量名，value 是赋给变量的值。如果 value 不包含任何空白符（例如空格、Tab缩进等），那么可以不使用引号；如果 value 包含了空白符，那么就必须使用引号包围起来。使用单引号和使用双引号也是有区别的。赋值号的周围不能有空格。  

Shell 变量的命名规范和大部分编程语言都一样：  

- 变量名由数字、字母、下划线组成；
- 必须以字母或者下划线开头；
- 不能使用 Shell 里的关键字（通过 help 命令可以查看保留关键字）。
###使用变量
使用一个定义过的变量，只要在变量名前面加美元符号`$`即可，如  

	author="严长生"
	echo $author
	echo ${author}
变量名外面的花括号{ }是可选的，加不加都行，加花括号是为了帮助解释器识别变量的边界，比如下面这种情况：  

	skill="Java"
	echo "I am good at ${skill}Script"
推荐给所有变量加上花括号{ }，这是个良好的编程习惯。
###修改变量的值
已定义的变量，可以被重新赋值，如：

	url="http://www.liuzhengjun.com"
	echo ${url}
	http://www.liuzhengjun.com
	url="http://www.liuzhengjun.com:81"
	echo ${url}
	http://www.liuzhengjun.com:81
第二次对变量赋值时不能在变量名前加$，只有在使用变量时才能加$。
###单引号和双引号的区别
以单引号' '包围变量的值时，单引号里面是什么就输出什么，即使内容中有变量和命令（命令需要反引起来）也会把它们原样输出。这种方式比较适合定义显示纯字符串的情况，即不希望解析变量、命令等的场景。

以双引号" "包围变量的值时，输出时会先解析里面的变量和命令，而不是把双引号中的变量名和命令原样输出。这种方式比较适合字符串中附带有变量和命令并且想将其解析后再输出的变量定义。  
###将命令的结果赋值给变量
Shell 也支持将命令的执行结果赋值给变量，常见的有以下两种方式：  
	
	variable=`command`  
	variable=$(command)
第一种方式把命令用反引号包围起来，反引号和单引号非常相似，容易产生混淆，所以不推荐使用这种方式；第二种方式把命令用$()包围起来，区分更加明显，所以推荐使用这种方式。
###只读变量
使用 readonly 命令可以将变量定义为只读变量，只读变量的值不能被改变。  
下面的例子尝试更改只读变量，结果报错：

	#!/bin/bash
	myUrl="http://www.liuzhengjun.com"
	readonly myUrl
	myUrl="http://www.liuzhengjun.com:81"
运行脚本，结果如下：  
`/bin/sh: NAME: This variable is read only.`  
###删除变量
使用 unset 命令可以删除变量。语法：  
`unset variable_name`  
变量被删除后不能再次使用；unset 命令不能删除只读变量。  

举个例子：

	#!/bin/sh
	myUrl="http://www.liuzhengjun.com"
	unset myUrl
	echo $myUrl
上面的脚本没有任何输出。  
###变量类型
运行shell时，会同时存在三种变量：  
#####局部变量
局部变量在脚本或命令中定义，仅在当前shell实例中有效，其他shell启动的程序不能访问局部变量。
#####环境变量
所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其正常运行。必要的时候shell脚本也可以定义环境变量。
#####shell变量
shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行