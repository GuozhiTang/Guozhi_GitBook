# 1.1 Java Environment Settings

## For Windows 10

*  Control Panel --&gt; System
*  Advanced System Settings
*  Environment Variables
*  In System Variables, create Java\_Home:

```text
"C:\Program Files\Java\jdk-11.0.1(address)"
```

*  Then create CLASSPATH:

```text
".;%Java_Home%\lib;%Java_Home%lib\tool.jar"
```

*  Then Edit Path: add the first line:

```text
 " "%Java_Home%\bin;%Java_Home%\jre\bin;" "
```

*  and add the last line:

```text
"C:\Program Files\Java\jdk-11.0.1(address)\bin"
```

*  Last, add the line:

```text
"%CLASSPATH%"
```

*  cmd:

```text
java -version; java; javac
```

