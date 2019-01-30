# Q & A

## 1. IntelliJ IDEA 出现" java: 程序包javax.servlet不存在、 java: 程序包javax.servlet.annotation"等错误

原因：IntelliJ IDEA 没有导入 servlet-api.jar 这个.jar包，需要手动导入。

导入步骤如下：

* 选中项目，右击选择“Open Modules Settings”，选择“Libraries”，点击“+”，选“Java”
* 在弹出的窗口中选择tomcat所在的目录，在lib目录下找到servlet-api.jar这个jar包导入完成即可。

