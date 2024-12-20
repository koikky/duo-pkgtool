# duo-pkgtool
A simple pkg tool for duo to pack RT-Thread.                 

## 1. 准备工作
- 首先需要拉取 `duo-pkgtool` 工具到本地目录。示例如下：
	``` shell 
	$ git clone git@github.com:koikky/duo-pkgtool.git 
	```
                   
- 同时，在使用之前，我们需要安装一些额外的外部依赖，示例如下:                           	
	``` shell
	$ sudo apt update
	$ sudo apt install u-boot-tools
	```

## 2. 开始使用
### 2.1. 设置环境
- 每次使用前，需要加载 `script/` 目录下的 `tool.sh`。示例如下：                                    
	``` shell
	$ cd duo-pkgtool
	$ source script/tool.sh 
	```  
                                                
- 同时，用户可以在终端里输入 `print_usage` 命令获取使用提示。示例如下：                                      
	``` shell 
	$ print_usage
	```                        

### 2.2. 打包
- 当成功运行 `tool.sh` 后，可以使用如下命令进行打包，打包结果为镜像文件。                                   
  	其中，命令的格式为：```mkpkg DPT_PATH_KERNEL={kernel} [DPT_BOARD_TYPE={type}] [DPT_PATH_OUTPUT={output}] [-l/-a]```，示例如下：                                              
	``` shell
	$ mkpkg DPT_PATH_KERNEL=/home/{username}/rt-thread DPT_BOARD_TYPE=duo256m -a 
	```                             
	- 携带的参数没有顺序之分。                                                                                                              
	- 参数中含有 `[]` 的项是可以省略的，只有选项 `DPT_PATH_KERNEL` 是不能省略的，打包时需要指定。                                                                
	- 被省略的项采用默认值：                                                                           
		（1）选项 `DPT_BOARD_TYPE` 的默认采用 `duo256m`。                                         
		（2）选项 `DPT_PATH_OUTPUT` 的默认采用目录 `duo-pkgtool/output`。                                                 
		（3）默认只对大核进行打包，若用户有其他选择可添加选项 `-l` 或 `-a`， `-l` 表示只对小核进行打包，`-a` 表示对全部进行打包。                                                                                                                                                                                                       
	
