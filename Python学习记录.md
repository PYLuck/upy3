# 一. LInux 

版本：Ubuntu，CentOS，Redhat

虚拟机软件：VMware Workstation版安装包--虚拟机-操作系统Ubuntu

* ### **安装Ubuntu系统**：

  软件工具 rufus-3.15.exe： http://rufus.ie/zh/ 

  Ubuntu系统：https://ubuntu.com/

  安装步骤（双系统）：https://www.bilibili.com/video/BV11k4y1k7Li

  双系统启动设置：**sudo update-grub**

  https://blog.csdn.net/jyqxerxes/article/details/80355343

  Ubuntu安装Pycharm：https://www.bilibili.com/video/BV16N411R7GC

  ​	细节：1.解压，2.bin目录下**$ ./pycharm.sh**

  创建pycharm快捷方式：https://blog.csdn.net/qq_20515461/article/details/90745100
  
* ### **配置环境Rec：**

  显卡：AMD Radeon R5 M230    显存：2G
  (base) pyl@PYL:~$ which conda
  /home/pyl/Anaconda3/bin/conda
  (base) pyl@PYL:~$ which python
  /home/pyl/Anaconda3/bin/python
  (base) pyl@PYL:~$ ipython
  Python 3.7.4 (default, Aug 13 2019, 20:35:49) 

  ###### conda环境管理：
  删除：conda remove --name tf2 python=3.7
  查看环境：conda info -e


  ###### 先创建一个名为torchCpu19虚拟环境：
  conda create -n torchCpu19 python=3.7
  ```ubuntu
  # # To activate this environment, use
  #     $ conda activate torchCpu19
  
  # To deactivate an active environment, use
  #     $ conda deactivate
  ```

  ###### 官网安装pytorch ==1.9.1
  conda install pytorch torchvision torchaudio cpuonly -c pytorch 

  ENV包括：
  tensorflow 1.15.0	#tf2
  tf==2.1.0		#tf1
  pytorch==1.9.1		#torchCpu

  * tf1.15在其compat.v2模块中包含2.0 API的完整实现。其能够使用enable_v2_behavior()函数模拟2.0行为

  * Ubuntu下解决Pycharm无法正常输入中文的问题

  https://blog.csdn.net/m0_54032194/article/details/119081008

* ### ==**#的3种使用方法及其含义**==

  * #### # 注释内容

  * #### 编码方式

    ```python
    #_*_coding:utf-8_*_   表示指定文件编码格式
    ```

  * ####  解释器路径

    ```python
    #!/home/pyl/Anaconda3/bin/python3    
    #!/python解释器的路径：用于操作系统直接执行文件选择的解释器
    ```

    

## 1.目录结构

只有一个根目录 /   不分盘符

 /bin :可执行二进制文件的目录

/etc ：系统配置文件的目录

/home :用户家目录

### 1.1 目录指令

**ls**  查看当前目录下的信息

pwd  查看当前目录

tree   查看多层目录信息		tree 文件夹名

clear

#### 1.1.1 切换目录指令

cd 目录	   切换到指定目录

==cd ~==			切换到当前用户的**主目录**

cd ..			切换到上一级目录

cd .			 切换到**当前目录**

==cd -==				切换到上一次的目录

#### 1.1.2 绝对路径与相对路径

1. 绝对路径切换到桌面(两次TaB键显示提示：当前目录下有哪些东西)

   cd /home/blackey/Desktop

2. 相对路径

   cd ../Desktop

#### 1.1.3 增删 文件及目录

touch 文件名			#增        

* 1以绝对路径创建  touch  /.111.txt

* 2创建多个：touch  1.txt  2.txt  3.txt

mkdir 目录名				#创建文件夹    -p  创建依赖文件夹

* mkdir  A/B  **-p**   # A不存在时仍可创建A、B

rm 文件名		#默认删文件   

* 删除目录名：**rm 目录名 -r**    #删除非空目录
* 删除前**询问**：rm 1.txt **-i**
* 删除，文件不存在则忽略： rm 1.txt **-f**

rmdir 目录名				#删除空目录==rm  -d

#### 1.1.4 复制、移动 文件及目录

cp     复制			# cp  1.txt  AA    

* 拷贝目录及其内容： **cp  AA CC -r**
* 显示拷贝后的路径描述： cp  AA  BB  **-v**
* **保留文件的原有权限**不丢失，也可拷贝文件夹：**-a**     （主要针对cp to**其他用户**）        

mv    移动，重命名		# mv AA CC

* 显示路径：-v

#### 1.1.5 重定向命令

 在终端显示的信息在文件里保存 

">"   相当于w操作：如 ls  >  ./Info.txt

**">>"  追加模式写入信息：ls  >> ./Info.txt**

追加写入自定义内容： echo  "自定义内容"  >>  file1

#### 1.1.6 查看文件内容

cat    查看（多个）小型文件

* 管道  |    用于临时查看，不保存

  如 ls  /bin  |  cat			# 管道相当于临时保存终端的容器

gedit    打开文件

more  	分屏查看大型文件

### 1.2 终端命令格式

**command**  [-options] [parameter]

* scp命令要求先[-opt]再参数

* 1.短选项 ：-r

  2.长选项：--help

查看命令帮助：

* --help  或 man

 ls命令选项使用：

-l    ：以列表方式显示

-h   ：以大小单位显示，默认字节

-a	：显示隐藏文件和目录

ls -alh   ==  ls  -a  -h  -l

**ll == ls -la**

e.g.   **d**rwxrwxr  3  blackey blackey 4.0k  10月  AA

​          **-**rwxrwxr    **-** 表示普通文件     **d** 表示目录

说明：**文件类型**用户权限 硬链接数 用户名 用户组  文件大小 修改时间 文件名

### 1.3 软链接与硬链接

* **软链接（快捷方式）  	ln -s   源文件(绝对路径)  快捷方式名**

  use： ln -s    /home/blackey/桌面/ a.txt    ../a_s.txt

  文件类型：l     .......    a_s.txt  ->  a.txt

* 硬链接 （源文件的别名）      In  源文件    别名

  use： ln     a.txt    a-h.txt    #删除源文件,仍然能通过别名访问

### 1.4 文本搜索 &查找
* **搜索(在文本中)**: 	**grep  '搜索内容'   文件地址  -n**

  ​								-i   忽略大小写； -n  显示匹配行号；  -v 搜索内容取反 

* 结合正则表达式：      ^ : 以指定字符串开头；   $ : 以指定字符串结尾；    .   : 匹配一个非换行符的字符

  ​								grep   '^d'    Note.txt   -n        : 以d 开头的行搜索

  ​								grep  's$'    Note.txt  -n

​                                       grep  'd.s'    Note.txt  -n        :用  .  替换字符，如查找des

查询文件名： 如 ls ./bin | grep '文件名'				#引号可以不加 

* **查找**：**find  ./   -name  '11.txt'**

  * 通配符：    *    代表0个或多个任意字符；     ？  代表任意1个字符

    ​			如： find  .  -name    1?.txt             # 用通配符，不能加引号

    

### 1.5  压缩&解压

支持格式：  .gz     .bz2  ;       .zip(压缩出来容量较大)

use:    tar(压缩和解压缩)  : ==tar -zcvf  test.tar.gz   *.txt==   (压缩)      解压：tar -zxvf   test.tar.gz 

​		(只支持解压到指定目录：tar -zxvf  test.gar.gz  -C File1)

​			tar   -c   创建打包文件；  -x   解包

​					 -v 显示包里的文件    -f   指定文件名称，放在最后用

​					-z    压缩或解压；    -C       解压到指定目录

​		# 针对 .bz2文件的解压：tar  -==j==xvf   test.bz2

​			zip     		zip  testz.zip  *.txt

​			unzip  -d		:  (解压到指定目录)



### 1.6  **权限**--文件&用户

* 修改文件权限： chmod   u-r  1.txt

  ​											u :user    g:grop   o:othet  a:all user     

     + ​                                    + :增加权限     -：撤销权限       = ：设置权限 

     + 权限包括：                 r, w, ==**x(可执行)**==， -  （无权限）

       

* chmod   u+x    fx.py            

* 执行前需要先声明解释器：

  which Python    >>  /home/pyl/Anaconda3/bin/python3

  ==**#!/home/pyl/Anaconda3/bin/python3**==

* ==**执行文件：./fx.py**==

  ####  <u>**chmod  777  file.txt    (数字法，777为最高权限，全部可读写执行)**</u> 

反之为000: ---

r  :4    w: 2    x : 1   - :0       **rwx: 7**



### 1.7  管理员权限(whoami)

* sudo -s   进入管理员       root@PYL:~/Desktop#

  exit                                   pyl@PYL:~/Desktop$

  passwd  修改密码

  关机与重启：shutdown -h now          reboot

* **1.==创建用户组==**

sudo  groupadd    用户组名    

修改用户主组：sudo usermod  -g  用户组名   用户组名1

删除用户组：  sudo gropedel  用户组名



* **2.**==**useradd   创建用户**==

  sudo useradd -m  -g  pyler     创建用户及主目录      -g 设置主组

  sudo passwd  pyler    指定用户设置密码

  su  -  pyler    切换用户

  * **修改用户信息**：usermod       -G  设置一个附加组        -g   修改用户组
  * **sudo usermod  -G  sudo pyler**      # 第二个sudo为附加组名称

* userdel     删除用户

  sudo userdel -r  pyler



### 1.8 SSH远程登录及操作

apt list | grep openssh-server     # （服务器端）查看软件是否安装

客户端(cmd):  ssh  -Vss

远程拷贝：    scp  1.txt  pyl@111.xxx.xxx.xxx:/home/pyl/Desktop       # 本地远程拷贝至服务器

​						scp   pyl@111.xxx.xxx.xxx:/home/pyl/Desktop/1.txt   ./			#拷贝至本地

[拷贝文件夹需要 -r ]：  scp -r  



### 1.9 Vim编辑器（命令编辑）

* **命令模式**(默认)   →(i) 编辑模式       esc                →(:) 末行模式     esc

* 编辑模式 （ i ）

* 末行模式   ( : )  

* 保存&退出：    wq 或 x      不保存强制退出：q!

  * 其他指令：

    yy    复制光标所在行                      dd   删除光标所在行

    **u    撤销                     					ctrl+r   反撤销                  p   粘贴**

    G   回到最后一行          				gg  回到第一行

​         搜索：在末行模式：/搜索内容        下一个：n

​		修改： :26，29s/Hello/Hi                #限定从26-29行的Helllo替换成Hi

#### 1.10  软件安装及卸载(Ubuntu)

* 离线安装：(包.deb)

  sudo dpkg   -i   包.deb   

* 在线安装：apt-get

​       sudo apt-get install  安装包 

查看所有安装文件：   **apt  list**



* 卸载软件

sudo dpkg  -r  安装包名    （通过离线安装包软件的卸载）

sudo apt-get remove 包名



————————————————————————————————————

————————————————————————————————————————

# 二. Numpy与Pandas

## 1.1 Numpy

* N维数组-ndarray

ndarray.shape		数组维度的元组

ndarray.size			元素的数量

ndarray.itemsize	一个元素的长度(字节)

* 创建数组

  a = np.array([ [1,2],[2,3] ] , [ [3,4],[5,6] ])		# 三维数组，shape（高2,  行2，列3）

* 指定数组类型(不指定默认int64，小数默认float64)

  如 np.object_		:Python对象

  a = np.array( [ [1,2],[2,3] ] , [ [3,4],[5,6] ], **detype=np.float32**)

  a = np.array(['tensor', 'torch', 'python'], **detype=np.string_**)

* 生成数组：

  1. 0,1数组

  f0 = np.ones([4,8]);	np.zeros()

   np.one_like(f0)		#按f0的维度生成

  2. f= np.array([ [1,2],[2,3] ] , [ [3,4],[5,6] ] );	# 深拷贝

  3. np.asarray(f)                                            #浅拷贝

  4. 生成指定范围：

     np.linspace(0,100,**10**)     # 从0-100等间隔生成10个数  num

     np.logspace(0,100,**2**)     # 0-100等2间隔生成	step

* 生成随机数组

  np.random(2,3)     # 2行3列随机数组

  **均匀分布--**

  #均匀分布的方差:值越大，数据越集中，瘦高

  ​	np.random.rand(d0,d1,...dn)      #返回[0,1)内一组均匀分布的数

  ​	np.random.randint()

  ​	np.random.uniform(low=0, high=1,size=（3,5）)      #从一个均匀分布[low,high)中随机采样，生成一个3行5列的数组
  
  **正态分布**--api
  
* np.random.normal()

  

* 数组索引，切片

  [*, #]

* 形状修改：

  1. 对象.reshape       # 产生新变量

  2. 对象.resize           # 对原值更改

  3. 对象.T                  #  行列互换

     

* 类型修改

  对象.astype()

* 数组去重

  np.unique()

#### 1.2 ndarray运算

1. 逻辑运算

   stock = np.random.normal(0, 1, (8, 10) )

   qiepian = stock[0:5, 0:5]       #5行5列的值

   qiepian[qiepian >1] =2         # 大于1的值赋值为2      $$大于小于直接判断，满足要求直接赋值

2.  通用判断函数

    np.all()							# 所有要求满足才返回True

   np.any()					#满足任意要求返回True

   

3. 三元运算符   

   np.where(val >0, 1 ,0)    # val>0则赋值1，否则赋值0
   
   ```Python
   np.where(np.logical_and(val >0.5, val<1),1,0)   # 同时满足>0.5且<1赋值为1
   np.where(np.logical_or())     # 或
   ```

4. 统计指标

   val.max(axis=1)  # 按行求最大值

   val.argmax(axis=1)      #求行最大值的下标

   midian()     #中位数

   mean()    std()  #  标准差

   var()      # 方差 

#### 1.3 矩阵运算

```python
arr = np.array([1,3,5,7,9])
arr += 1			# [2,4,6,8,10]
```

* 数组与数组的运算----需要满足**广播机制**
  * 维度相等
  * shape，相对应的位置为1

若：

​			A(3), B(3)      维度相等，可以运算

​		A(  , 2, 1)

​		B(8, 1, 3),    相对位置维度为1，可以运算，

​	res(8, 2, 3)

```python
arr1 = np.array([[1],[2]])          # shape(2,1)
arr2 = np.array([[1,2,3],[5,6,1]])  # shape(2,3)
print(arr1+arr2)        # 可以运算，ans[[2,3,4],[7,8,3]]，shape(2,3)
```

* 矩阵乘法

  np.matmul(A, B)

  np.dot(A, B)        #区别：==dot支持矩阵*数字==



## 2.1 Pandas





# 三 商品物体检测项目



* 迁移学习：模型任务相似，旧的领域训练好的模型，应用于新的模型
  * 方法： fine tuning（微调）
    * 已训练好的模型：Pre-trained model

TF的预训练模型：Inception V1-4    Inception-ResNet-v2   ResNet v1-2

​		 * 过程	 

### 3.1 读取图片数据ImageDataGenerator()

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.python.keras.preprocessing.image import ImageDataGenerator
```

* train_gen = ImageDataGenerator() 

  生产图片的批次张量值，提供数据增强

  * rescale = 1.0 / 255,  # 标准化
  * zca_whitening = False    # 针对图片进行PCA降维，减少冗余
  * width_shift_range # 默认水平平移

* flow(x_train, y_train, batch_sz)    # 如minister数据集的读取

* **本地数据集**读取的方法：

  ==flow_from_directory==(directory===path==, target_size=(h, w), batch_size, **class_mode='binary'**, shuffle=True)

  **class_mode='binary'** 表示目标值的格式为1D label

  ​						categorical    表示2D one-hot encoded labels

  **path**的目录格式为固定的：**data**/**train**/dogs/内容；cats/内容；...



#### 3.1.1 notop模型

* 是否包含最后的3个全连接层，专用于做fine-tune

  ```python
    from tensorflow.python.keras.applications.vgg16 import VGG16
      # 在__init__中添加
      # VGG在imagenet比赛中预训练的权重，使用resnet训练
      self.base_model = VGG16(weights='imagenet',include_top=False)
  ```

  05第四节  04.21













++++++++++++++++++未完待续+++++++++++++++++







## 四.  Git与Github

**安装git**： sudo apt-get install git

#   工作区--暂存区--仓库区-~-服务器（GitHub）

在工作区增删改：git  add 文件或目录；git rm 文件；  git  checkout  -- 文件 

工作区到暂存区：git   add   login.py

暂存区到仓库区：  git commit  -m  "备注"

==工作区直接到仓库区： git   commit  -am   "备注"==



### 4.1 Git单人本地仓库

* 创建仓库

  git init

  ctrl +h  显示隐藏文件夹   .git  

  $$创建用户信息:

  **git config user.name PYL**

  git config user.email   zaixiadouing@qq.com

  $$ touch   login.py

  ==git status;     git add .  ;   git commit -m  "登录仓库完成";        git log==

  
  
  ```shell
  pyl@PYL:/media/pyl/HDD_disk/Gitclub$ git status
  位于分支 master
     尚无提交
     未跟踪的文件:
    （使用 &quot;git add &lt;文件&gt;...&quot; 以包含要提交的内容）
  	login.py
     提交为空，但是存在尚未跟踪的文件（使用 &quot;git add&quot; 建立跟踪）
     
  ## 跟踪所有文件，提交到暂存区
  pyl@PYL:/media/pyl/HDD_disk/Gitclub$ git add .   
  位于分支 master
  尚无提交
  要提交的变更：
    （使用 "git rm --cached <文件>..." 以取消暂存）
  	新文件：   login.py
  	
  ## 提交到仓库区
  pyl@PYL:/media/pyl/HDD_disk/Gitclub$ git commit -m  "登录仓库完成"
  [master （根提交） 79d8e03] 登录仓库完成
   1 file changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 login.py
   
  ## 查看信息
  pyl@PYL:/media/pyl/HDD_disk/Gitclub$ git log
  commit 79d8e031b887170f40e4d70ff21c6c48ac67a0aa (HEAD -> master)
  Author: PYL <zaixiadouing@qq.com>
  Date:   Sun Oct 17 16:47:27 2021 +0800
      登录仓库完成
  ```
  
  回退版本：   git  reset  --hard  HEAD^       #    一个^  表示向前回退一个版本 ，，或HEAD~4  ，回退4个版本
  
  查看所有版本：git   reflog        # 当前为git  log
  
  ```shell
  79d8e03 (HEAD -> master) HEAD@{0}: reset: moving to HEAD^
  ae34583 HEAD@{1}: commit: 优化更新
  79d8e03 (HEAD -> master) HEAD@{2}: commit (initial): 登录仓库完成
  ```
  
  回退到指定版本：git  reset  --hard     ae34583
  
  
  
  从暂存区回退到工作区：git  checkout   login.py
  
  
  
  
  
  从服务器到本地 ：git clone https://github.com/PYLuck/upy3.git
  
  
  
  上传： git push    

























