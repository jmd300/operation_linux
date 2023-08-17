# profile、bashrc、bash\_profile区别

## 1. profile

profile，路径：`/etc/profile`，用于设置系统级的环境变量和启动程序，在这个文件下配置会对所有用户生效。

当用户登录（login）时，文件会被执行，并从`/etc/profile.d`目录的配置文件中查找shell设置。

一般不建议在`/etc/profile`文件中添加环境变量，因为在这个文件中添加的设置会对所有用户起作用。

当需要添加时，可以按以下方式添加：

```sh
export JAVA_HOME=/opt/module/jdk8
export PATH=$PATH:$JAVA_HOME/bin
```

添加时，可以在行尾使用`;`号，也可以不使用。

一个变量名可以对应多个变量值，多个变量值需要使用`:`进行分隔。

添加环境变量后，需重新登录才能生效，也可使用 source 命令强制立即生效：

```shell
source /etc/profile
```

查看是否生效可以使用 echo 命令：

```sh
echo $JAVA_HOME
```

## 2. bashrc

bashrc 文件用于配置函数或别名。bashrc 文件有两种级别：

* **系统级**: 系统级的位于`/etc/bashrc`，对所有用户生效。
* **用户级**: 用户级的位于`~/.bashrc`，仅对当前用户生效。

bashrc 文件只会对指定的 shell 类型起作用，bashrc 只会被 bash shell 调用。

## 3. bash\_profile

`bash_profile`只对单一用户有效，文件存储位于`~/.bash_profile`，该文件是一个用户级的设置，可以理解为某一个用户的 profile 目录下。

这个文件同样也可以用于配置环境变量和启动程序，但只针对单个用户有效。

和 profile 文件类似，bash\_profile 也会在用户登录（login）时生效，也可以用于设置环境变理。

但与 profile 不同，bash\_profile 只会对当前用户生效。



