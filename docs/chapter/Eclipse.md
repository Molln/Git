# Eclipse

### 一 将工程初始化为本地库

工程→右键→Team→Share Project→Git

Create Repository

Finish

### 二 Eclipse 中忽略文件

1 Eclipse 特定文件

这些都是 Eclipse 为了管理我们创建的工程而维护的文件，和开发的代码没有直接关系。最好不要在 Git 中进行追踪，也就是把它们忽略。

* .classpath 文件
* .project 文件
* .settings 目录下所有文件

2 为什么要忽略 Eclipse 特定文件呢？

同一个团队中很难保证大家使用相同的 IDE 工具，而 IDE 工具不同时，相关工程特定文件就有可能不同。如果这些文件加入版本控制，那么开发时很可能需要为了这些文件解决冲突。

3 GitHub 官网样例文件

https://github.com/github/gitignore

https://github.com/github/gitignore/blob/master/Java.gitignore

4 编辑本地忽略配置文件，文件名任意

````
# Compiled class file 
*.class

# Log file 
*.log

# BlueJ files 
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar 
*.war 
*.nar 
*.ear 
*.zip
*.tar.gz 
*.rar

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*

.classpath
.project
.settings
target
````

5 在~/.gitconfig 文件中引入上述文件

````
[core]
excludesfile = C:/Users/Lenovo/Java.gitignore
````

[注意：这里路径中一定要使用“/”，不能使用“\”]

### 三 推送到远程库

### 四 Oxygen Eclipse 克隆工程操作

### 五 Kepler Eclipse 克隆工程操作

### 六 解决冲突

冲突文件→右键→Team→Merge Tool
修改完成后正常执行 add/commit 操作即可