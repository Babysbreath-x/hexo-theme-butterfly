#### 0 git 分支相关命令

\# 1.查看所有分支

 git branch -a

\# 2.查看当前使用分支(结果列表中前面标*号的表示当前使用分支)

git branch

\# 3.切换分支

git checkout 分支名

\# 4.创建gh-pages分支：

git checkout --orphan gh-pages



#### 1 我的博客搭建流程

1. 创建仓库，[username.github.io](http://username.github.io/)；

2. 创建两个分支：master 与 hexo；

3. 设置hexo为默认分支（因为我们只需要手动管理这个分支上的Hexo网站文件）；

4. 使用git clone [git@github.com](mailto:git@github.com):username/username.github.io.git拷贝仓库；

5. 将刚才 hexo 本地生成博客的文件夹下的所有文件，都拷贝到，username.github.io 文件夹下[在分支source下操作]；
   或[username.github.io下的所有文件拷贝到，刚才 hexo 本地生成博客的文件夹下]，再用github客户端,Add本地库；

   (或在本地username.github.io文件夹下通过Git bash依次执行npm install hexo、hexo init、npm install 和 npm install hexo-deployer-git（此时当前分支应显示为hexo）)

6. 修改_config.yml中的deploy参数，分支应为master；

7. 依次执行git add .、git commit -m “…”、git push origin hexo提交网站相关的文件；

8. 执行hexo generate，hexo deploy生成网站并部署到GitHub上。

这样一来，在GitHub上的username.github.io仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页。

#### 2 日常修改

在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理：

1. 依次执行git add .、git commit -m “…”、git push origin hexo指令将改动推送到GitHub（此时当前分支应为hexo）；
2. 然后才执行hexo generate -d发布网站到master分支上。

虽然两个过程顺序调转一般不会有问题，不过逻辑上这样的顺序是绝对没问题的（例如突然死机要重装了，悲催…的情况，调转顺序就有问题了）。

#### 2.2 本地资料丢失

当重装电脑之后，或者想在其他电脑上修改博客，可以使用下列步骤：

1. 使用git clone [git@github.com](mailto:git@github.com):CrazyMilk/CrazyMilk.github.io.git拷贝仓库（默认分支为hexo）；
2. 在本地新拷贝的CrazyMilk.github.io文件夹下通过Git bash依次执行下列指令：npm install hexo、npm install、npm install hexo-deployer-git（记得，不需要hexo init这条指令）。