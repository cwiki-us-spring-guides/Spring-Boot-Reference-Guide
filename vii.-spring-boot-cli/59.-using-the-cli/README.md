# 59. 使用CLI

一旦安装好CLI，你可以输入`spring`来运行它。如果不使用任何参数运行`spring`，将会展现一个简单的帮助界面：

```text
$ spring
usage: spring [--help] [--version]
       <command> [<args>]

Available commands are:

  run [options] <files> [--] [args]
    Run a spring groovy script

  ... more command help is shown here
```

你可以使用`help`获取任何支持命令的详细信息，例如：

```text
$ spring help run
spring run - Run a spring groovy script

usage: spring run [options] <files> [--] [args]

Option                     Description
------                     -----------
--autoconfigure [Boolean]  Add autoconfigure compiler
                             transformations (default: true)
--classpath, -cp           Additional classpath entries
-e, --edit                 Open the file with the default system
                             editor
--no-guess-dependencies    Do not attempt to guess dependencies
--no-guess-imports         Do not attempt to guess imports
-q, --quiet                Quiet logging
-v, --verbose              Verbose logging of dependency
                             resolution
--watch                    Watch the specified file for changes
```

`version`命令提供一个检查你正在使用的Spring Boot版本的快速方式：

```text
$ spring version
Spring CLI v1.4.1.RELEASE
```

