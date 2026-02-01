# CEGUI vcpkg 移植项目

本项目目标是在尽量不修改原始源代码的情况下，使旧的 CEGUI 和其工具能够使用现代版本的库进行编译。

## 特性

- **依赖管理**：通过 vcpkg 自动处理依赖关系
- **无源码修改**：尽量不修改原始代码的前提下在新版本的库中编译通过
- **编辑器工具**：包含 CELayoutEditor 和 CEImagesetEditor

## 安装

### 第一步：安装 vcpkg

如果尚未安装 vcpkg：

```bash
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
./bootstrap-vcpkg.sh
```

### 第二步：安装依赖

使用 vcpkg 安装所需的依赖：

```bash
./vcpkg install wxwidgets:x86-windows-static 
./vcpkg install freetype:x86-windows-static
./vcpkg install pcre:x86-windows-static 
./vcpkg install glew:x86-windows-static
```

**注意**：安装过程可能需要一些时间，因为 vcpkg 会从源码构建依赖项。

### 第三步：构建 CEGUI

克隆此仓库并构建项目：

```bash
git clone <仓库地址>
cd cegui-vcpkg
mkdir build && cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=[vcpkg路径]/scripts/buildsystems/vcpkg.cmake -A Win32
cmake --build .
```
