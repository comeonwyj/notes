> 全局配置 

    git config --global user.name "username"
    git config --global user.email "xxx@qq.com"

> 初始化本地仓库

    cd d:
    mkdir localpro
    cd localpro

    git init

> 创建文件,添加本地记录

    touch test.txt
    echo 11111 >> test.txt
    cat test.txt
    
    git add test.txt 
    git commit [filename] -m "test.txt append 11111"

*windows系统会出现编码更改信息:*

    git config --global core.autocrlf false

1. 当设置成true时，这意味着你在任何时候添加(add)文件到git仓库时，git都会视为它是一个文本文件(text file)。它将把crlf变成LF。
2. 当设置成false时，line endings将不做转换操作。文本文件保持原来的样子。
3. 设置为input时，添加文件git仓库时，git把crlf变成lf。当有人Check代码时还是lf方式。因此在window操作系统下，不要使用这个设置。

- windows下：CRLF（表示句尾使用回车换行两个字符，即windows下的"\r\n"换行）
- unix下：LF（表示句尾，只使用换行）
- mac下：CR（表示只使用回车）
  
> 要经常查看状态,看有无修改文件,并查看哪里有修改,根据情况登记(add)并提交(commit)

    echo 22222 >> test.txt
    cat test.txt
    git status
    git diff test.txt

    git add test.txt
    git commit test.txt -m "test.txt appended '2222'"
    git log [filename] [--pretty=oneline]

    git reflog [filename]

>根据Log文件及其描述,回退版本信息

    git reset --hard HEAD^ //回退到上一版本,linux
    git reset --hard "HEAD^" //windows下

    git reest --hard HEAD~n //都可以,n为数字,为回退几步

    git reset --hard commitId //根据Log显示的commitid 回退

> 撤销修改

    //撤销未登记前的改动,及在上一次add后文件做了更改,这命令把这些更改撤销
    echo 3333>>test.txt
    cat test.txt
    git checkout -- test.txt 
    cat test.txt
    //撤销登记后未提交前(暂存区)的改动
    echo 4444>> test.txt
    cat test.txt
    git add test.txt
    git reset HEAD test.txt

> 删除文件

    //工作区删除
    rm test.txt
    //这时工作区和版本库就不一样了,分两种情况
    1.确实要从版本库中删除该文件
    git rm test.txt
    git commit -m "remove test.txt"
    2.文件被删错了。因为版本库里有,从版本库恢复
    git checkout -- test.txt

> 创建github远程仓库(例如:testpro),关联本地仓库

    ssh-keygen -t rsa 
    //一路回车,根据创建出来的路径,打开.pub文件
    把里面的东西全部copy给github的SSH keys

    git remote add origin git@github.com/username/testpro.git

> 重要! 先要和本地合并一下,再推送给远程备份
    git pull origin master 
    //出错 fatal: refusing to merge unrelated histories,加参数
    git pull origin master --allow-unrelated-histories

    git push -u origin master


