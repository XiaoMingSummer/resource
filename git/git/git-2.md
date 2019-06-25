# Git -版本控制工具

## 分支
- 查看分支：`git branch`，当前分支会标有一个`*`

- 创建分支：`git branch [分支名称]`
    + 分支中的代码，与创建那一刻主分支中的内容完全相同

- 切换分支：`git checkout [分支名称]`

- (简写)创建并切换分支：`git checkout -b [分支名称]`

- 合并分支：`git merge [分支名称]`，即：将其他分支合并到当前分支。这里需要注意的是，建议将其它分支合并到主分支

- 删除分支：`git branch -d [分支名称]`

### 合并分支冲突
- 注意：合并分支时出现冲突只能手动处理文件，然后，再次提交

```
如果在一个从分支中做了修改，然后，在主分支中也做了修改。
此时，将这个从分支合并到主分支的时候，就会出现合并冲突的问题！


在两个分支中同时修改了一个文件中的内容，此时，就会造成合并分支冲突
，如果发生了合并冲突，需要我们手动解决！

1 决定保留哪个分支中的内容
2 重新提交


操作：将 hotfix 分支，合并到cart分支中

HEAD：表示当前分支
hotfix： 表示被合并分支

<<<<<<< HEAD
        <span>第三次修改的内容</span>

        <cart>这是在 cart 分支中提交的内容</cart>
=======
        <span>第三次修改的内容 --- hotfix 修改bug</span>
>>>>>>> hotfix
```

### 分支的说明
- 1 公司开发的项目都是由多个分支组成：主分支 + dev分支
- 2 项目经理新建项目仓库，所有的程序员都从这个仓库中获取代码，完成开发任务
- 3 项目经理：搭建设计仓库，创建master分支，以及dev分支（以及 debug分支等）
- 4 所有的程序员在 dev分支 上进行开发，并且还有自己维护的分支
- 5 程序员在分支上完成开发任务后，会提交合并请求
- 6 项目经理安排测试，如果没有问题了，最后才会与 master 分支合并


## github
- [github官网](https://github.com/)
- [开源中国-Git](https://git.oschina.net/)

```
在 GitHub 上免费托管的 Git 仓库，
任何人都可以看到喔（但只有你自己才能改）。
所以，不要把敏感信息放进去。
```

### github与git
- 1 git 是一个版本控制工具
- 2 github就是一个网站，这个网站提供了 git 服务器的功能

### 将代码提交到远程仓库（HTTPS）
- 1 在本地创建仓库
    + `git init`
    + `git config`
- 2 新建 README.md 文件，并输入任意内容
- 3 将 README.md 提交到本地
    + `git add`
    + `git commit`
- 4 在github中新建仓库，并拿到仓库地址
- 5 使用命令 `git push [仓库地址] master` 提交内容到github的默认分支
- 6 刷新github仓库页面，在线修改 README.md 文件，并提交
- 7 使用命令 `git pull [仓库地址] master` 获取仓库中的最新内容


### 获取远程仓库内容
- 命令：`git pull [仓库地址] [分支名称]` 获取远程仓库最新内容

- 命令：`git clone [仓库地址] [自定义本地仓库名]` 将整个仓库克隆到本地
    + 实例：`git clone git://github.com/jquery/jquery.git myJQ`

### 简化操作
- 1 `git remote add origin [仓库地址]`
    + 作用：使用origin代替 仓库地址 ，方便操作
    + origin就相当于js的变量，[仓库地址]就相当于变量的值
- 2 `git push -u origin master`
    + 作用：`-u`参数将origin与master连在一起
- 3 使用简化命令 `git push origin` 就代替原来："git remote add origin [仓库地址]"


### SSH介绍
- 非对称加密、公钥和私钥

```
GitHub 需要识别出你推送的提交确实是你推送的，而不是别人冒充的，
而 Git 支持 SSH 协议，所以，GitHub 只要知道了你的公钥，
就可以确认只有你自己才能推送，从而省去每次输入密码的操作。

可以同时设置多个SSH key，比如：你可以在公司电脑提交需要一个key，
回家后自己的电脑提交也需要一个key

ssh是一种安全的传输模式
github要求推送代码的用户是合法的，所以每次推送时候都要输入账号密码，
用以验证你是否为合法用户，为了省去每次都要输入密码的步骤，采用shh公钥，密钥
也就是你说的sshkey来验证你是否为合法用户
在你的电脑生成了一个唯一的ssh公钥和私钥，公钥放到github上面，当你推送的时候，git就会
匹配你的私钥是否跟github上面的公钥是配对的，正确就认为你是合法的，允许推送。

sshkey可以理解为是你的身份标识，放在github上面表明你是这个项目的一个开发人员，但是别
人是可以截获的，你本机的私钥别人就无法截获，sshkey就可以保证每次传输都是安全的。
```

### 将代码提交到远程仓库（SSH）
- 1 创建SSH Key：`ssh-keygen -t rsa`
- 2 在文件路径 `C:\用户\当前用户名\` 找到 `.ssh` 文件夹
- 3 文件夹中有两个文件：
    + 私钥：`id_rsa`
    + 公钥：`id_rsa.pub`
- 4 在 `github -> settings -> SSH and GPG keys`页面中，新创建SSH key
- 5 粘贴 公钥 `id_rsa.pub` 内容到对应文本框中
- 6 在github中新建仓库或者使用现在仓库，拿到`git@github.com:用户名/仓库名.git`
- 7 此后，再次SSH方式与github“通信”，不用输入密码确认身份了
