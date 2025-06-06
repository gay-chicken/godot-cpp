# godot-cpp 模板
这个仓库提供了一个 Godot 4.0+ 的 GDExtension 快速开始开发模板。

## 内容
* 一个空的 Godot 项目 (`demo/`)
* godot-cpp 作为子模块 (`godot-cpp/`)
* GitHub Issues 模板 (`.github/ISSUE_TEMPLATE.yml`)
* GitHub CI/CD 可在创建发布版本时发布库软件包 (`.github/workflows/builds.yml`)
* 提前配置好的 GDExtension C++ 开发源文件。 (`src/`)

## 使用方法
要使用此模板，请登录 github 并点击版本库页面顶部的绿色 “Use this template ”按钮。
这样您就能创建一个具有完整 git 历史记录的版本库副本。请确保克隆了正确的分支，因为这些分支是为各自的 Godot 开发分支的开发而配置的，彼此之间存在差异。请参阅文档了解各版本之间的变化。

克隆您自己的副本到本地计算机后，要开始使用，您应该 

* 修改你的库名称
  * 通过修改 `libname` 字符串，更改 `SConstruct` 文件中已编译库文件的名称。
  * 修改 `demo/bin/example.gdextension` 文件中要加载的库名称的路径名。将 `libgdexample` 替换为 `SConstruct` 文件中指定的名称。
  * 修改 `demo/bin/example.gdextension` 文件的名称
* 更改 `demo/bin/your-extension.gdextension` 文件中的 `entry_symbol` 字符串，使其配置为 GDExtension 名称。这应该与 `GDExtensionBool GDE_EXPORT` 外部 C 函数相同。顾名思义，这将设置 GDExtension 的入口函数，以便由 Godot 编辑器 C API 加载。
* 在 `register_types.cpp` 文件的初始化方法（此处为 `initialize_gdextension_types`）中注册您希望 Godot 与之交互的类，语法为 `ClassDB::register_class<CLASS-NAME>();`。