# g
[![GoDoc](https://godoc.org/github.com/voidint/g?status.svg)](https://godoc.org/github.com/voidint/g)
[![Go Report Card](https://goreportcard.com/badge/github.com/voidint/g)](https://goreportcard.com/report/github.com/voidint/g)

`g`是一个命令行工具，可以提供一个便捷的多版本[go](https://golang.org/)环境的管理和切换。


## 特性
- 支持列出可供安装的go版本号
- 支持列出已安装的go版本号
- 支持在本地安装多个go版本
- 支持卸载已安装的go版本
- 支持在已安装的go版本之间自由切换

## 安装
### 自动化安装
敬请期待

### 手动安装
- 下载对应平台的二进制压缩包。
- 将压缩包解压至`PATH`环境变量目录下，如`/usr/local/bin`。
- 编辑shell环境配置文件（`~/.bashrc`、`~/.zshrc`...）

    ```shell
    $ cat > ~/.bashrc <<EOF
    export GOROOT=~/.g/go
    export PATH=~/.g/go/bin:$PATH
    export G_MIRROR=https://golang.google.cn/dl/
    EOF
    $ source ~/.bashrc
    ```

## 使用
查询当前可供安装的`stable`状态的go版本

```shell
$ g ls-remote stable
1.11.9
1.12.4
```

安装目标go版本`1.12.4`

```shell
$ g install 1.12.4
installed successfully
$ go version
go version go1.12.4 darwin/amd64
```


查询已安装的go版本

```shell
$ g ls
1.12.4
```

查询可供安装的所有go版本

```shell
$ g ls-remote
1
1.2.2
1.3
1.3.1
...    // 省略若干版本
1.11.7
1.11.8
1.11.9
1.12
1.12.1
1.12.2
1.12.3
1.12.4
```

安装目标go版本`1.11.9`

```shell
$ g install 1.11.9
installed successfully
$ go version
go version go1.11.9 darwin/amd64
```

切换到另一个已安装的go版本

```shell
$ g ls
1.11.9
1.12.4
$ g use 1.12.4
go version go1.12.4 darwin/amd64

```

卸载一个已安装的go版本

```shell
g uninstall 1.11.9
Uninstall successfully
```
## FAQ
- 环境变量`G_MIRROR`有什么作用？

    由于中国大陆无法自由访问Golang官网，导致查询及下载go版本都变得困难，因此可以通过该环境变量指定一个镜像站点（如`https://golang.google.cn/dl/`），g将从该站点查询、下载可用的go版本。

- 支持源代码编译安装吗？

    不支持

- 支持Linux、macOS、Windows下使用吗？

    暂未支持Windows。

## 鸣谢
感谢[nvm](https://github.com/nvm-sh/nvm)、[n](https://github.com/tj/n)、[rvm](https://github.com/rvm/rvm)等工具提供的宝贵思路。