1、声明
	首先这里再明确一下，所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。
	不幸的是，Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动的，前面我们举的例子只是为了演示，如果要真正使用版本控制系统，就要以纯文本方式编写文件。
	因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的UTF-8编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。
2、命令git checkout -- readme.txt
	意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
	一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
	一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
	总之，就是让这个文件回到最近一次git commit或git add时的状态。
	场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
	场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
3、创建SSH key
	在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

	ssh-keygen -t rsa -C "youremail@example.com"

	然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。
	如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
/*****************命令*****************/
   git init
   git add [文件名]
   git commit -m ["备注"]
   git diff
   git reset --hard HEAD^/[HEAD~100前100个版本]/[ak293版本号前面几个]
   /*HEAD指针指向的版本就是当前版本*/
   git reflog 记录每一次命令
   git checkout -- file
        命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令
   git rm [<options>] [--] <file> 从版本库中删除某文件
   git remote add origin ...git   添加远程仓库
   git push -u origin master 
   		由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。只要本地作了提交，就可以通过命令：git push origin master 操作
   git checkout -b dev 
   		创建一个新的分支dev，-b表示创建并切换，这一句相当于下面两句
   		git branch dev
   		git checkout dev
   git branch 查看当前所有的分支









