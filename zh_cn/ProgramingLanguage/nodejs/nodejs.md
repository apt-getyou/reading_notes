## 安装nodojs

由于 GitBook 是基于 Node.js 开发的，所以依赖 Node.js 环境。如果您的系统中还未安装 Node.js，请点击下面的链接，根据你所使用的系统下载对应的版本。如果已安装则略过本步骤。

  * [Node.js 下载页面](https://nodejs.org/en/download/stable/)  

  * Windows 版和 Mac 版的 Node.js 都是常规的安装包，连续下一步安装即可。  

  * Linix 版可以参照官方文档通过 `yum`  `apt-get` 之类的工具安装，也可以通过源码包安装，如下所示：

  ```bash
  $ wget https://nodejs.org/dist/v5.4.1/node-v5.4.1.tar.gz
  $ tar zxvf node-v5.4.1.tar.gz
  $ cd node-v5.4.1
  $ ./configure
  $ make
  $ make install
  ```

## 使用淘宝镜像 [官网](https://npm.taobao.org/)

  * 由于某不可描述的原因，在中国大陆访问node官方源异常缓慢，所以需要使用淘宝提供的国内加速源提高npm的下载速度  

    >淘宝镜像是一个完整 npmjs.org 镜像，你可以用此代替官方版本(__只读__)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。

  * 使用说明

    - 你可以使用我们定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm:
    ```bash
    $ npm install -g cnpm --registry=https://registry.npm.taobao.org
    ```

    - 或者你直接通过添加 npm 参数 alias 一个新命令:
    ```bash
    alias cnpm="npm --registry=https://registry.npm.taobao.org \
    --cache=$HOME/.npm/.cache/cnpm \
    --disturl=https://npm.taobao.org/dist \
    --userconfig=$HOME/.cnpmrc"
    ```

    - Or alias it in .bashrc or .zshrc
    ```bash
    $ echo '\n#alias for cnpm\nalias cnpm="npm --registry=https://registry.npm.taobao.org \
      --cache=$HOME/.npm/.cache/cnpm \
      --disturl=https://npm.taobao.org/dist \
      --userconfig=$HOME/.cnpmrc"' >> ~/.zshrc && source ~/.zshrc
    ```

  * 安装模块

  从 registry.npm.taobao.org 安装所有模块. 当安装的时候发现安装的模块还没有同步过来, 淘宝 NPM 会自动在后台进行同步, 并且会让你从官方 NPM registry.npmjs.org 进行安装. 下次你再安装这个模块的时候, 就会直接从 淘宝 NPM 安装了.

  ```bash
  $ cnpm install [name]
  ```

  * 同步模块

    直接通过 sync 命令马上同步一个模块, 只有 cnpm 命令行才有此功能:

    ```bash
    $ cnpm sync connect
    ```

    当然, 你可以直接通过 web 方式来同步: /sync/connect
    ```bash
    $ open https://npm.taobao.org/sync/connect
    ```

  * 其它命令

    支持 npm 除了 publish 之外的所有命令, 如:
    ```bash
    $ cnpm info connect
    ```
