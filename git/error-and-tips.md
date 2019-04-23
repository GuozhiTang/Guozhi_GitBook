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

