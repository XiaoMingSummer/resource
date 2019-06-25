# Shell 介绍

- Shell：壳（区别于：核）
- 普通意义上的shell就是可以接受用户输入命令的程序。它之所以被称作shell是因为它隐藏了操作系统底层的细节。
- Bourne-Again shell（bash）：应用非常广泛的一种shell工具，是一个命令处理器，bash也是大多数Linux系统默认的Shell。


## 常用 shell 命令
```bash
# change directory 改变目录
cd 01-教学资料 # 进入到 01-教学资料 文件夹
# cd .. 				 # 返回上一级目录

# list 展示当前目录列表
ls
# ls -l 	# 以列表的形式展示目录
# ls -a 	# 展示全部目录
# ls -al 	# 相当于 ls -a -l
# ls -al 01-教学资料 	# 展示 01-教学资料 中所有的目录

# 打印当前目录
# print work directory
pwd

# 清空当前窗口内容
clear

# 创建文件夹
mkdir 文件夹名称
# mkdir js css images # 同时创建多个文件夹

# 创建文件
touch 文件名称
# touch css/index.css

# 查看文件全部内容
cat 文件名称
# 按 q 键退出查看 

# 查看文件部分内容
less 文件名称
# 内容太多，可以按 空格键 查看剩余内容
# 查看到最后，需要按 q键 退出查看

# 删除文件
rm 文件名称
rm -r css

# 删除空文件夹
rmdir 文件夹名称

# 移动文件（相当于剪切）
mv 文件名称 目标目录
# mv index.html css/pipixia.html # 移动的同时，修改文件名称
# mv index.html demo.html # 重命名

# 复制文件
cp 文件名称 新文件名称
# cp index.html js/index1.html

# 自动补全 按：tab键
# 如果有多种情况，连按两次 tab键 会把所有的文件名称打印出来

# 重定向 将内容 Hello-World 添加到 test.txt 文件中
echo Hello-World > test.txt
# ls > test.txt 	# 覆盖，将ls命令的结果输出到 test.txt 文件中
# ls >> test.txt 	# 追加
```

# vi编辑器
## 3种模式yy
- 2 插入模式

- 3 底行模式

- 每种模式，能够执行的操作是不同的

  ![vi](media\vi.png)

## 插入模式
- 在命令模式下，输入`i`或`a`，就可以进行编辑了

## 底行模式
```bash
# 使用 vi
vi 文件路径

# 保存
:w 
# :w filenme #另存为

# 退出
:q

# 保存并退出
:wq

# 撤销更改，返回到上一次保存的状态
:e!

# 不保存强制退出
:q!

# 展示行号
:set nu
# 删除行号 
:set nonu
第一种是，手动显示：在vim命令行模式下输入  ：set nu

  取消显示：在vim命令行模式下输入：  set nonu

第二种是，永久自动显示：我们修改一个配置文件。

我们输入命令：vim   ~/.vimrc

打开后是一个空文件，我们添加 set nu，保存退出，再次进入vim编辑器，就会自动显示出行号了。大笑如此简单
```

## 命令模式
```bash
# 保存并退出，大写
ZZ

# 撤销操作，可多次使用
u

# 删除当前行
dd

# 复制当前行
yy

# 粘贴内容
p

# 向前翻页
ctrl+b

# 向后翻页
ctrl+f

# 进入编辑模式，
i #当前光标处插入
a #当前光标后插入
A #光标移动到行尾
o #当前行下面插入新行
O #当前行上面插入新行
```

