# 环境变量

1.  **/etc/profile** 或 **/etc/profile.d/\*.sh**

    &#x20;      其中定义的环境变量适用于系统上所有用户。编辑这些文件需要 root 权限。当用户登录时，会首先读取 `/etc/profile` 文件，然后执行 `/etc/profile.d/` 目录中所有以 `.sh` 结尾的脚本文件。其中定义的环境变量会在用户登录时生效，\
    &#x20;      对于已经登录的用户，修改了 `/etc/profile` 或 `/etc/profile.d/*.sh` 文件后，环境变量不会立即生效，只有在下次登录时才会应用新的配置或者使用source /etc/profile刷新环境变量。\
    而系统启动时，不会重新读取 `/etc/profile` 和 `/etc/profile.d/*.sh` 文件来设置环境变量。在系统启动过程中，更常见的是使用 `/etc/environment` 文件来设置全局的环境变量。
2.  \~/.bash\_profile、\~/.bash\_login或\~/.profile\
    \~/.bash\_profile、\~/.bash\_login 和 \~/.profile 是在用户登录时执行的 Bash shell 配置文件，用于个人级别的环境变量和配置。

    这些文件之间的区别在于它们的加载顺序和适用范围：

* \~/.bash\_profile： 这是最常见的配置文件，通常用于定义个人的特定于 Bash shell 的配置。当用户登录时，Bash 会首先尝试读取 \~/.bash\_profile 文件，并在成功读取后立即停止查找其他文件。因此，如果存在 \~/.bash\_profile 文件，会忽略后面两个文件。推荐使用 \~/.bash\_profile 来配置个人的环境变量和自定义命令。
* \~/.bash\_login： 如果没有找到 \~/.bash\_profile 文件，Bash 会尝试读取 \~/.bash\_login 文件。它的作用类似于 \~/.bash\_profile，但相对较少使用。
* \~/.profile： 如果既没有 \~/.bash\_profile 也没有 \~/.bash\_login 文件，Bash 将会读取 \~/.profile 文件。这是一个通用的配置文件，不仅用于 Bash shell，也可以在其他类 Unix 系统中使用。它适用于大多数情况下，无论用户使用何种登录方式。

如果同时存在 \~/.bash\_profile 和 \~/.profile，Bash 通常只会读取 \~/.bash\_profile。因此，建议在个人配置中优先考虑使用 \~/.bash\_profile。

需要注意的是，对于已经登录的用户，修改了 \~/.bash\_profile、\~/.bash\_login 或 \~/.profile 文件后，环境变量不会立即生效，只有在下次登录时才会应用新的配置。或者使用source 刷新。
