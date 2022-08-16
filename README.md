# git-help
- [git 常用命令](https://docs.dingtalk.com/i/nodes/Xzr6RBgD3LYJnrgnZ5ZMJZPnyElvd7e9?nav=mySpace&navQuery=spaceId%3Dvr4zEyoMygRarzDY&iframeQuery=utm_source%3Dportal%26utm_medium%3Dportal_myspace_file_tree)

# Git 入门教程

## Git 简介

- [Git 的诞生](https://www.liaoxuefeng.com/wiki/896043488029600/896202815778784)。
- [集中式 vs 分布式](https://www.liaoxuefeng.com/wiki/896043488029600/896202780297248)。
- [安装 Git](https://www.liaoxuefeng.com/wiki/896043488029600/896067074338496)。
- [创建版本库](https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304)。

## 时光机穿梭

- 版本回退。

    git log 查看 Git 提交记录，但是当我们回退过版本之后，可能之前的 commitId 查询不到时，结合 `git reflog` 进行查看。

    ```shell
    git reset --hard HEAD^
    ```

- 工作区暂存区。

    Git 和其他版本控制系统如 SVN 的一个不同之处就是有暂存区的概念，第一步是用 `git add` 把文件添加进去，实际上就是把文件修改添加到暂存区，第二步是用 `git commit` 提交更改，实际上就是把暂存区的所有内容提交到当前分支，你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。期间可以使用 `git status` 查看当前暂存区的状态，同时 Git 回明确告诉我们哪些文件做过什么样的修改。

- 管理修改。

    每一次的修改因为文件都处于暂存区，所以需要进行 `git add` 操作，通过使用 `git commit` 将暂存区的文件一次性提交到分支操作。

- 撤销修改。
    - 情况 1：

        自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态或已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

        ```shell
        git checkout --file
        ```

    - 情况 2：

        现在假定是凌晨 3 点，你不但写了一些胡话，还 `git add` 到暂存区了。

        ```shell
        git reset HEAD <file>
        ```

- 删除文件。
    - 情况 1：

        本地删除完文件 commit 以及 push 将远端文件删除。

    - 情况 2：

         使用 `git rm file` 之后进行 commit 操作，此时如果想回复删除也可以通过 `git checkout --file` 来进行恢复。

## Git 基本语法

- clone 项目。

    ```shell
    git clone git@*.git
    ```

- 将工作区文件添加到暂存区。

    ```shell
    git add .
    ```

- 将暂存区文件提交到本地分支。

    ```shell
    git commit -m "commit message"
    ```

- push 项目。

    ```shell
    git push
    ```

## 分支管理

- 创建与合并分支。
    - 创建分支。

        创建分支的形式并不唯一，通常我们可以通过 `git branch branchname` 来完成分支的创建，同时也可以使用 `git checkout -b branchname` 或者 `git switch -c branchname` 来完成创建以及切换到新的分支，补充 `git branch -d branchname` 可以用来删除分支。

    - 合并分支。

        合并分支的意思就是将我们改完的 bug 分支代码合并到我们的共享分支如：dev 分支，此时我们可以通过 `git merge bug-001` 的方式进行分支的合并。

- 解决冲突。

    当合并代码是发生冲突是很常见的问题，首先不要慌，可以使用 `git status` 查看哪些文件是冲突的，解决提交即可，补充 `git log --graph` 可以查看分支合并图。
    
- [git rebase](https://blog.csdn.net/gg1229505432/article/details/121958413)
