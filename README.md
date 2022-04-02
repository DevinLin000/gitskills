# GitSkills  ---关于git的一些常用命令

-   可能遇到的陌生英语单词

    -   modified \-\-\-- 被调整，被修改

    -   Untracked \-\-\-- 未跟踪; 未跟踪状态; 未追踪;

    -   reset \-\-\-- 调整; 重新设置; 重新安置; 将...恢复原位;

    -   merge \-\-\-\--(使)合并，结合，并入; 相融; 融入;
        渐渐消失在某物中;

-   git add \"文件名\" 该命令把文件添加到仓库 \<相当于线下>

    -   `<file>`{=html} 可以替换成文件名。比如readme.txt

         ![](https://api2.mubu.com/v3/document_image/e1656584-abc5-4c62-85a2-757bc07d1475-11752736.jpg)

         ![](https://api2.mubu.com/v3/document_image/458c81b5-17c9-446e-8166-7ba832160246-11752736.jpg)

    -   git
        commit命令，-m后面输入的是本次提交的说明（相当于备注），可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

    -   实例

         ![](https://api2.mubu.com/v3/document_image/3dac8298-0b69-4b2c-a546-9c0d12e28ded-11752736.jpg)

-   ```git commit -m \"文件名\" 该命令把文件提交到仓库 \<相当于线上>```

-   git status 命令可以让我们查看仓库当前的状态.
         ![](https://api2.mubu.com/v3/document_image/e163d884-a2a7-4fbb-845c-eac9d05b6fed-11752736.jpg)

-   git diff 可以让我们查看difference，能看具体修改了什么内容。

-   git log 命令可以显示从最近到最远的提交日志

-   版本回退

    -   HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git
        reset \--hard commit_id。

    -   穿梭前，用git
        log可以查看提交的历史内容，以便确定要回退到哪个版本。【这里确定先版本内容】

    -   要重返未来，用git
        reflog查看命令历史，以便确定要回到未来的哪个版本。git
        reflog会展示您每一个版本的commit
        id。【这里获取对应版本的commit id 以便返回版本】

-   工作区和暂存区

    -   工作区就是放文件的地方，比如本电脑的learngit文件夹

    -   暂存区是一个虚拟的东西，git add
        命令添加文件后，都处于暂存区。

    -   使用git add 后

       ![](https://api2.mubu.com/v3/document_image/38fe8ebf-beb2-48ab-9b2c-143ac3240e85-11752736.jpg)

    -   使用git commit 后

       ![](https://api2.mubu.com/v3/document_image/17adfbab-03b7-4589-9f16-046692f0199d-11752736.jpg)

-   管理修改

    -   第一次修改 -\> git add -\> 第二次修改 -\> git add -\> git
        commit

-   撤销修改

    -   git
        reset命令既可以回退版本，也可以把暂存区的修改回退到工作区

    -   场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git
        checkout \-- file。

    -   场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git
        reset HEAD
        `<file>`{=html}，就回到了场景1，第二步按场景1操作。

    -   场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。解决方法：用git
        log 查看提交的历史内容（日志），然后用git
        reflog查询对应的版本号，最后用git reset \--hard commit_id
        来穿梭版本。

-   删除文件

    -   命令git
        rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**。

-   添加数据库

    -   要关联一个远程库，使用命令git remote add origin
        git\@server-name:path/repo-name.git；

    -   关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名；

    -   关联后，使用命令git push -u origin
        master第一次推送master分支的所有内容；

    -   此后，每次本地提交后，只要有必要，就可以使用命令git push
        origin master推送最新修改；

    -   分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！

-   从远程库克隆数据库

    -   要克隆一个仓库，首先必须知道仓库的地址，然后使用git
        clone命令克隆。

    -   Git支持多种协议，包括https，但ssh协议速度最快

-   创建和合并分支

    -   git
        checkout命令加上-b参数表示创建并切换，相当于以下两条命令：

        -   \$ git branch dev

        -   \$ git checkout dev

    -   git merge命令用于合并指定分支到当前分支。

    -   Git鼓励大量使用分支：

    -   **查看分支**：git branch

    -   **创建分支**：git branch `<name>`{=html}

    -   **切换分支**：git switch `<name>`{=html}

    -   **创建+切换分支**：git switch -c `<name>`{=html}

    -   **合并某分支到当前分支**：git merge `<name>`{=html}

    -   **删除分支**：git branch -d `<name>`{=html}

-   解决冲突

    -   当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

    -   解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

    -   用git log \--graph命令可以看到分支合并图。

-   分支管理策略

    -   Git分支十分强大，在团队开发中应该充分应用。

    -   合并分支时，加上\--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast
        forward合并就看不出来曾经做过合并。

        -   **语法：**\$ git merge \--no-ff -m \"merge with no-ff\"
            dev

-   用分支处理bug

    -   修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；

    -   当手头工作没有完成时，先把工作现场git
        stash一下，然后去修复bug，修复后，再git stash
        pop，回到工作现场；

        -   Git还提供了一个stash功能，可以把当前工作现场"储藏"起来，等以后恢复现场后继续工作

        -   git stash drop来删除；

    -   在master分支上修复的bug，想要合并到当前dev分支，可以用git
        cherry-pick
        `<commit>`{=html}命令，把bug提交的修改"复制"到当前分支，避免重复劳动。

-   Feature 功能分支

    -   开发一个新功能feature，最好新建一个分支；

    -   如果要丢弃一个没有被合并过的分支，可以通过git branch **-D**
        `<name>`{=html}强行删除。

-   多人协作

    -   多人协作的工作模式通常是这样：

        -   首先，可以试图用git push origin
            `<branch-name>`{=html}推送自己的修改；

        -   如果推送失败，则因为远程分支比你的本地更新，需要先用git
            pull试图合并；

        -   如果合并有冲突，则解决冲突，并在本地提交；

        -   没有冲突或者解决掉冲突后，再用git push origin
            `<branch-name>`{=html}推送就能成功！

        -   如果git pull提示no tracking
            information，则说明本地分支和远程分支的链接关系没有创建，用命令git
            branch \--set-upstream-to `<branch-name>`{=html}
            origin/`<branch-name>`{=html}。

        -   这就是多人协作的工作模式，一旦熟悉了，就非常简单。

    -   总结

        -   查看远程库信息，使用git remote -v；

        -   本地新建的分支如果不推送到远程，对其他人就是不可见的；

        -   从本地推送分支，使用git push origin
            branch-name，如果推送失败，先用git
            pull抓取远程的新提交；

        -   在本地创建和远程分支对应的分支，使用git checkout -b
            branch-name
            origin/branch-name，本地和远程分支的名称最好一致；

        -   建立本地分支和远程分支的关联，使用git branch
            \--set-upstream branch-name origin/branch-name；

        -   从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

-   Rebase

    -   rebase操作可以把本地未push的分叉提交历史整理成直线；

    -   rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

-   创建标签

    -   命令git tag
        `<tagname>`{=html}用于新建一个标签，默认为HEAD，也可以指定一个commit
        id；

    -   命令git tag -a `<tagname>`{=html} -m
        \"blablabla\...\"可以指定标签信息；

    -   命令git tag可以查看所有标签。

-   操作标签

    -   命令git push origin `<tagname>`{=html}可以推送一个本地标签；

    -   命令git push origin \--tags可以推送全部未推送过的本地标签；

    -   命令git tag -d `<tagname>`{=html}可以删除一个本地标签；

    -   命令git push origin
        :refs/tags/`<tagname>`{=html}可以删除一个远程标签

-   使用github

    -   在GitHub上，可以任意Fork开源仓库；

    -   自己拥有Fork后的仓库的读写权限；

    -   可以推送pull request给官方仓库来贡献代码。

-   使用gitee

    -   大体上和使用github一样，就是git是中文版的github，而且访问速度快。

-   自定义git

    -   \$ git config \--global color.ui true Git
        显示颜色，会让命令输出看起来更醒目

-   忽略特殊文件

    -   忽略某些文件时，需要编写.gitignore；

      ![](https://api2.mubu.com/v3/document_image/5fead668-eb5c-4a8e-bf39-685064fa930f-11752736.jpg)

    -   .gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！


