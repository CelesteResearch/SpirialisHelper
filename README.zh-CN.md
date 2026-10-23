[English](README.md) | [简体中文](README.zh-CN.md)

# SpirialisHelper

面向 Shared 运行库的本地重建规则。准备时从用户提供的原始压缩包读取 Mod 代码。

## 所需文件

- 已安装 [Everest 6580 稳定版](https://github.com/EverestAPI/Everest/releases/tag/stable-1.6580.0)的原始 Celeste 目录，保留其中的
  `Celeste.dll`、`FNA.dll`、`MMHOOK_Celeste.dll`、`MonoMod.Utils.dll` 和 `Mono.Cecil.dll`。
- 原始 **SpirialisHelper 1.0.8** 压缩包 `SpirialisHelper.zip`，可从
  [支持的版本压缩包](https://gamebanana.com/mmdl/965693)获取。
- Workspace、Shared 和 Tools 仓库；宿主环境要求见
  [工作区 README][workspace-readme-zh-cn]。

保持压缩包完整，无需提取 DLL 或修改代码。支持的压缩包及内部程序集哈希记录在
[mod-rebuild.json](mod-rebuild.json)。

将下载的压缩包命名为 `SpirialisHelper.zip`，放在原始游戏安装目录的 `Mods` 下。

## 文件摆放

```text
Workspace/
  Shared/
  Tools/
  Mods/
    SpirialisHelper/                 # 本仓库

Celeste/                    # 原始游戏安装目录
  Celeste.dll
  FNA.dll
  Mods/
    SpirialisHelper.zip
```

其他所需 Mod 压缩包也放在原始游戏安装目录的 `Mods` 下。

## 构建

在工作区目录使用 [Tools README][tools-readme-zh-cn] 中的宿主准备参数。
以下以 Godot 为例：

```powershell
pwsh ./Tools/Prepare.ps1 `
  -CelesteDirectory '/path/to/Celeste' `
  -AudioBankDirectory '/path/to/Desktop' `
  -Targets Godot `
  -IncludeHelpers
```

准备流程校验支持的输入版本、构建依赖，并将运行包放到
`Content/Celeste/Mods/SpirialisHelper.zip`。生成源码、工具和构建中间文件均保存在工作区已忽略的
`artifacts/` 目录内。

## 许可

见 [LICENSE](LICENSE) 和 [NOTICE.md](NOTICE.md)。本仓库不包含原游戏文件、Mod 原始压缩包
或本地生成的运行包。

[workspace-readme-zh-cn]: https://github.com/CelesteResearch/Workspace/blob/main/README.zh-CN.md
[tools-readme-zh-cn]: https://github.com/CelesteResearch/Tools/blob/main/README.zh-CN.md
