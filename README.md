# rufeng12345.github.io
我的第一个仓库
- 网上新建仓库，不添加任何内容
- 本地新建文件夹，和网上的存在的仓库最好重名
- 在新建的文件夹中打开命令提示行工具，执行‘git init’命令，作用是将文件夹制作成git空仓库。会生成一个隐藏的.git文件夹。以及创建一个分支叫master（原本网上创建仓库默认分支是main）
- 执行git branch -m main 将当前分支重命名成main
- 更新下文件夹里面的内容
- 将跟新的内容上传到远端仓库，·git add .· 
- ·git commit -m"留言"·
- 最后如果直接· git push ·的话会失败，因为远端和本地没有关联，需要关联
- 执行·git remote add origin https://github.com/YangluFover/0924.git· 给本地添加一个班远端的地址起名字叫origin
- 然后在·git push ·的话依然失败，因为远端是空仓库，什么都没有，所以需要给远端创建一个分支main并上传
- ·git push -u origin main·提交到远端（origin）的main，如果不存在则创建

### 添加ssh
#### 因为每次下载都是https的方式，所以每次上传都需要输入用户名密码，很麻烦，这种情况可以使用ssh方式处理和GitHub网站关联
- 在电脑任意位置打开命令工具
- 使用·cd ~·跳转到电脑用户主目录（储存的系统的配置）
- 使用·ssh-keygen·命令生成系统密钥（一直回车，直到看到 一个2048的图）
- 执行·cd .ssh/·进入到.ssh文件夹，执行·ls·，就会看到 私钥 id_rsa 和公钥   id_rsa.pub
- 执行cat id_rsa.pub 查看公钥的文本内容 然后右键复制
- 打开GitHub网站设置，找到 SSH and GPG keys，点击new ssh key，新建一个ssh key，起名字，将复制的公钥粘贴，保存。一个系统一个名字
- 添加好ssh之后，以后的关联GitHub的操作都可以使用ssh链接操作了。

### 多人合作
需要创建一个新的仓库，添加上内容，还需要添加合作的人员{打开仓库的设置，找到Manage access 添加合作人员）根据多个用户修改的内容分两种情况
1. 修改的内容和同事a的没有关系

			1.同事a 克隆了项目到本地，一顿操作，更新了项目，并上传了
			2.同事b也克隆了项目到本地，（克隆的事件在同事a更新上传之前），一顿操作，根据需改的内容不同分两种情况
		
			3.同事b正常操作，然后上传，但是会上传失败，提示更新被拒绝，远端存在本地不存在的工作（版本 ），你在				       更新之前要整合远程的工作，推荐使用git pull命令，
			4.执行git pull 命令拉取远端存在的优先于本地的更新，会弹出一个版本留言提示（因为两个版本：同事a提交的和自己未提交的，自动合并（两个版本没有冲突）成一个版本，让你提交自动合并的版本留言，直接使用shift+z+z保存留言即可
			5.执行git push 就可以提交更新了，因为所有的修改都缓存了，所有的版本都做好了。
			6.因此来说个人维护同一个仓库的同一个分支，需要不断的拉取远端的下更新（git pull）
 2. 修改的内容和同事a的有关系（修改同一个文件）
	
				 1.同事a 克隆了项目到本地，一顿操作，更新了项目，并上传了
				 2.同事b也克隆了项目到本地，（克隆的事件在同事a更新上传之前），一顿操作，根据需改的内容不同分两种情况		
			     3.同事b正常操作，然后上传，但是会上传失败，提示更新被拒绝，远端存在本地不存在的工作（版本 ），你在				       更新之前要整合远程的工作，推荐使用git pull命令，
			     4.执行 git pull 命令拉去远端存在的有先于本地的更新，拉起去完毕之后会提示自动合并失败，让你手动处理冲突，然后提交
			     5.当你手动解决冲突的时候，肯定修改了对应的内容，所以此次修改远端没有记录，需要使用git三步上传
### 提示
- 仓库不能嵌套仓库
- 命令行中不能在仓库之外操作
- 出现OpenSSL 的错误，是ssl认证问题，可以使用·git config --global http.sslVerify false’全局 忽略ssl 认证。
- 如果不小心在执行·git remote add origin...的时候输错网址 用·执行·git remote add origin·
- 删除本地仓库之前，先要保证本地的和网上的同步 ，可用给git status查看仓库的状态
- 第一次使用ssh链接下载的时候，会询问你当前网络是否安全，敲yes回车，告诉他安全。
-  当你删除了仓库或者某个文件夹的时候，命令行恰巧名利打开在被删除的文件夹，那么把所有相关的文件夹关闭，然后重新在对应的位置打开新的命令行。