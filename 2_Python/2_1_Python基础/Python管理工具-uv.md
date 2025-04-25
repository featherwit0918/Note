
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
```

```