# CEGUI vcpkg Port

The goal of this project is to enable compilation of the legacy CEGUI and its tools with modern library versions while minimizing modifications to the original source code.

## Features

- **Dependency Management**: Automated dependency handling via vcpkg
- **No Source Modifications**: Compile with modern library versions while keeping original code changes to a minimum
- **Editor Tools**: Includes CELayoutEditor and CEImagesetEditor

## Installation

### Step 1: Install vcpkg

If you don't have vcpkg installed:

```bash
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
./bootstrap-vcpkg.sh
```

### Step 2: Install Dependencies

Install required dependencies using vcpkg:

```bash
./vcpkg install wxwidgets:x86-windows-static 
./vcpkg install freetype:x86-windows-static
./vcpkg install pcre:x86-windows-static 
./vcpkg install glew:x86-windows-static
```

**Note**: The installation process may take some time as vcpkg will build dependencies from source.

### Step 3: Build CEGUI

Clone this repository and build the project:

```bash
git clone <repository-url>
cd cegui-vcpkg
mkdir build && cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=[path-to-vcpkg]/scripts/buildsystems/vcpkg.cmake -A Win32
cmake --build .
```
