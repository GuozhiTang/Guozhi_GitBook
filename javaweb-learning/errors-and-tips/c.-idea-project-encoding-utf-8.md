# c. IDEA Project Encoding: UTF-8

Sometime the console of IDEA could not display other language like Chinese.

Like this:

![](../../.gitbook/assets/image%20%2820%29.png)

Then we can solve following these steps:

## 1. Settings

*  在File -Setting中设置如下图所示 把IDE 和项目都设置成为UTF-8

![](../../.gitbook/assets/image%20%283%29.png)

## 2. Vmoptions file

* 若是Windows:
*  打开 intellij idea15的安装目录 的bin 文件夹下的idea.exe.vmoptions ，用记事本或者Notepad++打开，在文件末尾处添加 **-Dfile.encoding=UTF-8 如下图**

![](../../.gitbook/assets/image%20%2818%29.png)

![](../../.gitbook/assets/image%20%284%29.png)

* 若是MacOs:
*  找到 IntelliJ IDEA 的安装目录，进入`bin`目录下，定位到`idea.vmoptions`文件， 双击打开`idea.vmoptions`文件， 然后，在其中追加`-Dfile.encoding=UTF-8`代码

![](../../.gitbook/assets/image%20%288%29.png)

![](../../.gitbook/assets/image%20%285%29.png)

## 3. VM options

打开Run-Edit Configurations，在VM options 处添加如下图所示，然后应用保存，重启intelij idea,测试发现控制台输出的汉字不在是乱码了

![](../../.gitbook/assets/image%20%2823%29.png)

