# b. Intellj\_Configure Initial Structure

## 1. Create folders

在web/WEB\_INF 目录下创建两个文件夹：classes和lib  
classes用来存放编译后输出的class文件，lib用于存放第三方jar包

![](../../.gitbook/assets/image%20%2819%29.png)

## 2. Configure folder path

* File -&gt; Project Structure \(ctrl + shift + Alt + s\) 或者使用工具栏的快捷键 -&gt; 选择Modules -&gt; 选择Paths -&gt; 选择“Use module compile out path” -&gt; 将Outputpath 和Test output path 都设置为刚刚创建的classes文件夹

![](../../.gitbook/assets/image%20%289%29.png)

*  选择当前窗口的Dependencies -&gt; 将Module SDK选择为自己当前的SDK版本 -&gt;点击右边的 + 号 -&gt; 选择 “1 JARS or directories ...”

![](../../.gitbook/assets/image%20%282%29.png)

*  -&gt; 选择刚刚创建的lib文件夹 -&gt; OK

![](../../.gitbook/assets/image%20%2822%29.png)

*  -&gt; 选择Jar Directory -&gt; OK

![](../../.gitbook/assets/image%20%2814%29.png)

*  -&gt; Apply -&gt; OK

![](../../.gitbook/assets/image%20%2817%29.png)

## 3. Configure Tomcat

*  打开菜单Run -&gt; Edit Configurations...
*  点击 “+” ，选择 “Tomcat Server” -&gt; 选择“Local”
*  点击 "Application Server" 后面的 "Configure..."，弹出Application Servers窗口，在Tomcat Home 选择本地安装的tomcat目录 -&gt; OK
*  在"Run/Debug Configurations"窗口中，设置“HTTP port”和“JMX port”（默认值即可），点击Apply -&gt; OK，至此tomcat配置完毕（左边列表中tomcat图标上小红叉是未部署项目的提示，部署项目后就会消失）。
* 最终设置如下图：

![](../../.gitbook/assets/image%20%2810%29.png)

