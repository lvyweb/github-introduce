# Github 使用总结

## 仓库

### 假设本地有一个通过 `git init` 创建出来的仓库

需求：将这个本地仓库放到线上远程仓库。
1.git add .或者使用git --all添加全部文件  
2.git commit -m "版本更新信息"  
3. 在第三方托管服务那里新建一个空仓库  
4. 拿到空仓库的地址  
5. 使用 `git remote add abc https://github.com/itcast-aaa/hello.git`  
6. 使用 `git push abc master`  
7. 通过上面的操作之后，以后每次去 `push` 的时候都必须显示的写上 `git push 远端仓库地址别名 分支名称`  

如果不想每次  `push` 的时候都写那么长（没有多个远程仓库，也不需要频繁的去push不同的分支），
假设每次都是 `push` 到 abc master，那么可以通过 `git push --set-upstream abc master` (与远程仓库相关联，下次推送还是默认这个)去推送一次。  

那么在以后的 push 中，只要仓库地址没变、分支不变，就可以直接 `git push`。  

### 本地没有，线上有  

需求：想要获取远程仓库到本地

1.使用 `git clone 远程仓库地址`  
2.git init 初始化当前文件夹为可操控的git仓库  
3.git status 查看状态信息,显示更新内容  
4.git add --all 或者git add .或者git add 文件名 添加文件  
5.git commit -m "第一次提交"  
6.git push 推送到远端  

只要执行了上面的操作之后，git 会自动帮你通过网络去下载对应的远程仓库，
下载下来之后自动添加一个 remote，地址是你 clone 的那个地址，名字叫 origin。
之后只要你想要 push ，直接 git push 就可以了。原因是它已经自动帮你建立了上下游关系。


注意：如果出现中文乱码；使用git config --global 解决

## 多人协作

### 步骤

需求：A的项目想让B参与
1.登录A的github，找到settings--->collaborator--->添加(add)   
2.B会收到邮件，B同意协同开发  
3.git add .  
4.git commit -m "提交日志"  
5.git push origin master    
6.git pull 如果不是最新版本  从线上拉取最新版本  
 

#### 权限问题

对于这个权限，首先你需要在你公司所使用的第三方托管服务那里注册一个账号，
然后告诉你的源代码仓库管理员你的账号是多少，它会给你配置项目的访问提交权限，
它给你配置之后，你需要去你的当时注册的邮箱中收一封邮件，然后你同意参与该项目开发，
然后你才有该远程仓库项目协同权限。



### 冲突

 如果两个人提交有冲突，两个人商量，然后再提交。




## 与陌生人协同开发
1.把别人的代码fork一份到自己本地  
2.修改之后提交到自己远端  
3.发起pullrequest给所有者  
4.对方同意你的修改  
5.你成了项目贡献者之一  

