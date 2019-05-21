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

![](../.gitbook/assets/image%20%2855%29.png)

* 最好解决办法有一个是：**勾选强制覆盖已有的分支（可能会丢失改动），再点击上传，上传成功。**
* \*\*\*\*[**http://www.cnblogs.com/xwdreamer/archive/2012/05/29/2523958.html**](http://www.cnblogs.com/xwdreamer/archive/2012/05/29/2523958.html)\*\*\*\*

\*\*\*\*

