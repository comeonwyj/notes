换电脑后远程连接库，首先要看需要哪种协议？
## 一.https协议连接，则建好远程链接后，输入用户名和密码就可以了

> 1.准备工作

    git init
    git config --global user.name "username"
    git config --global user.email "youremail@xxx.com"
    git add somefile
    git commit -m "info"
    
> 2.关键地方 远程链接名称设置

    git remote add linkname https://github.com/username/resositoryname.git
    git push -u linkname [branch name] //这里执行时要求输入用户名和密码
    如果出现警告没有执行成功，是因为没有先pull,可以用-f 参数强制推送：
    git push -u linkname [branch name] -f
    
## 二.用ssh协议，需要用ssh-keygen命令生成密匙对，公匙要在远程库里添加上

> 1.准备工作参考上面

> 2.生成密匙对

    ssh-keygen -t rsa -C "youremail@qq.com"
    //一路敲回车会在c:/users/Administrator/.ssh/下生成密匙对
    
> 3.在远程库配置公匙

> 4.建立ssh协议链接快捷名称  

    git remote add linkname git@github.com:yourname/resositoryname.git
    git push -u linkname [branch name] -f
    

    