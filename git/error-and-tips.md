# Error & Tips

## 1. git push时出现`failed to push some refs to...` :

其中（Non-fast-forward）的出现原因在于：git仓库中已经有一部分代码，所以它不允许直接把代码覆盖上去，一般情况很有可能是README.md文件，于是我们有两种选择：

* 强推：`git push -f`，即利用强覆盖的方式用我们本地的代码替代git仓库内的内容
* 先把git的东西fetch到你本地然后merge后再push
  * `git fetch`
  * `git merge`
  * 以上两句命令等价于：
  * `git pull`

所以我们执行git pull --rebase origin master，这条命令的意思是把远程仓库中的更新合并到本地仓库中，--rebase的作用是取消掉本地仓库中刚刚的commit，并把它们接到更新后的版本仓库之中

但此时有可能会出现`Please move or remove them before you switch branches`的错误

若无错误则直接执行`git push origin master`即可正常上传

## 2. git pull出现`Please move or remove them before you switch branches`的错误：

有时候我们在checkout或者rebase的时候会出现`Please move or remove them before you switch branches`的错误

此时可以先备份当前项目内容，然后执行`git clean -d -fx`删除掉当前内容，然后再pull，最后粘贴回备份的项目内容后执行`git push origin master`

## 3. git pull出现`Pull is not possible because you have unmerged files.`

应该是因为local文件冲突了

引用：

{% hint style="info" %}
1.pull会使用`git merge`导致冲突，需要将冲突的文件resolve掉 `git add -u`, `git commit`之后才能成功pull.

2.如果想放弃本地的文件修改，可以使用`git reset --hard FETCH_HEAD`，FETCH\_HEAD表示上一次成功`git pull`之后形成的commit点。然后git pull.  
注意：

git merge会形成MERGE-HEAD\(FETCH-HEAD\) 。git push会形成HEAD这样的引用。HEAD代表本地最近成功push后形成的引用。
{% endhint %}

## 4. git push出现github上的版本和本地版本冲突:

* Update were rejected because the tip of your current branch is behind its remote counterpart...

![](../.gitbook/assets/image%20%2866%29.png)

* 最好解决办法有一个是：**勾选强制覆盖已有的分支（可能会丢失改动），再点击上传，上传成功。**
* \*\*\*\*[**http://www.cnblogs.com/xwdreamer/archive/2012/05/29/2523958.html**](http://www.cnblogs.com/xwdreamer/archive/2012/05/29/2523958.html)\*\*\*\*

## 5. \(Add\) Wrong Updates Revocation in Index Area \(Cache\)

In some cases, after running **`git add .`**, we might find that we updates wrong data to the index area.

* In order to do the revocation, we can check the updates in Index area:

```bash
git status
```

![](../.gitbook/assets/image%20%2848%29.png)

* We can use following command to cancel updates in index area. If **`<file>`** is not specified, then it means to cancel all the updates in index area.

```bash
git reset HEAD <file>
```

## **6.  \(Commit\) Wrong Updates Revocation**

After `git commit -am "xxxxxx"`, sometime we want to revocate it, then we should:

```bash
git reset --soft HEAD^
```

* Here we only revocate the commit operation, the code is still there
* `HEAD^` means the last version, which can also be written as `HEAD~1`
* So, if we want to revocate two commits, we can user `HEAD~2`

{% hint style="info" %}
* --mixed: 不删除工作空间改动代码，撤销commit，并且撤销git add .操作
  * 这个是默认参数，相当于没有写入参数
* --soft: 不删除工作空间改动代码，撤销commit，不撤销git add .
* --hard: 删除工作空间改动代码，撤销commit，撤销git add .
  * 注意，完成这个操作后，就恢复到了上一次的commit状态
{% endhint %}

## 7. \(Comments\) Wrong Updates Revocation

如果commit中的注释写错了，只是想改一下注释，则：

```bash
git commit --amend
```

此时会进入默认vim编辑器，修改完注释完毕后保存就好了

## 8. \(Push/Clone\) Permission denied \(publickey\). fatal: Could not read from remote repository. Please make sure you have the correct access rights and the repository exists.

* 情况一：和Github的连接不成功
  * 检测连接情况，若不成功，按照1.11 Git and Github Settings重新设置
  * ```bash
    ssh -T git@github.com
    ```
* 情况二：连接成功但是用SSH Clone的时候始终不成功
  * 改变方式，使用HTTPS方式连接Clone即可

## 9. \(Add\) error: unable to index file 'node\_modules/.bin/atob' fatal: updating files failed

* 此时进入 `node_modules/.bin` 查看其中的文件，都是不能open的
* 原因是这些文件是直接从github上clone下来的，而github上的这些文件是从MacOS push上去的，他们link的方法不一样，而这些文件都是link文件，所以没有办法打开
* 解决办法就是删除当前 `node_modules` 文件夹然后 `npm install` 重新生成，同时根据 `8.4 .gitignore`  生成 `.gitignore` 文件，这样可以减少操作系统冲突
* 具体可以继续研读 `Symbolic Link` 相关知识点

## 10. \(Add\) error: pathspec '.gitignore'' did not match any file\(s\) known to git

* 这个问题一般是文件或者文件夹的名称错误，由于该文件或者文件夹不存在引起的
* 所以需要重新确认输入命令中的各名称是否正确

## 11. \(Add/push\) error: unable to create temporary file: No such file or directory

```bash
git config --global core.fscache false
```

## 12. \(Merge\) error: you need to resolve your current index first

* 出现这种情况可能是因为有conflicts没有解决可以：
  * 解决conflicts后再次执行merge
  * 回退到merge前的版本

```bash
git reset --merge
```

