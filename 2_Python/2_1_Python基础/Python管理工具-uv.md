
**UV**（全称 Universal Virtual）是由 Astral 团队基于 Rust 语言开发的下一代 Python 包管理工具，旨在替代传统工具链（如 pip、virtualenv、poetry 等），提供 一站式解决方案。其核心目标是通过 极速性能 和 功能集成，解决 Python 开发中的依赖管理、环境隔离、多版本切换等痛点

### 核心特点
**极速性能**
- 基于 Rust 开发，依赖解析速度比传统工具（如 pip）快 10-100 倍，尤其在安装大型包（如 PyTorch、NumPy）时仅需几秒‌
**功能高度集成**
- 整合了 pip、virtualenv、poetry、pyenv、pipx、twine 等工具，提供一站式解决方案‌
- 支持虚拟环境管理、依赖锁定、Python 版本控制、脚本运行、工具安装及包发布‌
**统一的锁文件与工作区**
- 通过 uv.lock 文件精确锁定依赖版本，确保开发、测试和生产环境的一致性‌
- 支持 Cargo 风格的工作区（Workspaces），便于管理多模块项目‌
**跨平台支持**
- 兼容 macOS、Linux 和 Windows 系统，无需预装 Rust 或 Python 即可安装
‌
### 安装升级与卸载
**安装**
官方提供的安装方式很多, brew可以使用
```
brew install uv
```
**升级**
通过独立安装程序安装的时候可以使用下面的命令
```
uv self update
```
**卸载**
```
uv cache clean
rm -r "$(uv python dir)"
rm -r "$(uv tool dir)"
rm ~/.cargo/bin/uv ~/.cargo/bin/uvx
```
> 先清理缓存, 然后删除python和toll存储的文件夹, 最后删除uv和uvx命令

### 管理Python版本
```
uv python list       查看可用的python版本和已经安装的python版本, 这两个功能是一起的
uv python install    安装python版本, 可以多个版本一起安装
uv python find       查找某个python版本的路径
uv python pin        将当前版本固定为特定的python版本
uv python uninstall  卸载python版本
```
> 这些版本都是作用于项目的, 目前没有官方提供的设置到全局的方法, 所以python的版本管理可以结合pyenv来使用, uv刚好可以检测到系统里吗的所有的python版本


### 项目管理
**初始化项目**
```
uv init 路径
```
> 这会直接使用项目名称来创建一个项目, 也可以先创建项目的文件夹, 然后进入文件夹使用`uv init`来初始化项目
> 
> 注意初始化项目之后项目只是创建了一些配置文件和初始化文件而已, 还没有创建环境
> 
> 创建虚拟环境需要在初始化之后执行命令的时候才创建, 例如`uv sync`, 当然`uv run`和`uv lock`也可以
> 
> 注意如果在目标路径的父目录找到`pyproject.toml`, 项目会被添加为父目录的工作区成员。提供`no-workspace`可以避免

**init命令的主要选项**
- `--app`  为一个应用程序创建项目, 这是默认的行为, 默认的这个行为不是为了构建和分发为python包而设计的, 这种适合开发服务/脚本/命令行的等
- `--package`将项目设置构建为python包, 会定义项目等[build-system], 如果你给了`--lib`选项那么这是默认携带的, 也可以在使用`--app`时组合使用这个选项,  这将包含[project.scripts]入口点, 并使用`src/`项目
- `--lib` 创建一个库项目, 这个目标是为了包的构建和分发
- `--name` 项目名称, 默认是目录名称
- `--python/-p` 指定项目使用的python版本
- `--script`这个可以直接创建独立的脚本文件, 然后使用`uv run 脚本文件名`执行
> --app与--package的区别是package目录结构上会多一个src, 另一个上project.toml会多出project.scripts选项和build-system选项
> --lib 与 --package的区别不大, 看起来就是少了个project.scripts, 其他几乎一样

**添加依赖**
```
uv add 包名
```
主要参数
- `--dev`  添加到开发依赖项
- `--default-index` 默认软件包索引的url, 默认值是`https://pypi.org/simple`
- `--index`  在解析依赖项时使用的url, 除了默认索引之外
- `--reinstall`  重新安装所有的软件包, 无论他们是否已安装
- `--script` 将依赖项添加到指定的python脚本

**移除依赖项**
```
uv remove 包名
```
> 主要的参数和`add`一模一样

**同步项目依赖和配置**
```
uv sync
```
同步确保所有依赖项都已安装并且与锁定文件一致, 如果项目虚拟环境不存在则会被创建
**同步项目依赖和配置**
```

```