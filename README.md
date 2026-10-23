[English](README.md) | [简体中文](README.zh-CN.md)

# SpirialisHelper

Local rebuild recipes for the Shared runtime. Original Mod code is read from your own archive during preparation.

## Required files

- An original Celeste installation with **Everest 6580 stable**:
  [release](https://github.com/EverestAPI/Everest/releases/tag/stable-1.6580.0).
  Keep `Celeste.dll`, `FNA.dll`, `MMHOOK_Celeste.dll`,
  `MonoMod.Utils.dll` and `Mono.Cecil.dll` together.
- Original **SpirialisHelper 1.0.8**: `SpirialisHelper.zip`, available from the
  [supported archive](https://gamebanana.com/mmdl/965693).
- The Workspace, Shared and Tools repositories. Host requirements are described
  in the [workspace README][workspace-readme].

Keep the archive intact; do not extract its DLL or edit its code. The archive and
embedded assembly hashes are recorded in [mod-rebuild.json](mod-rebuild.json).

Save the downloaded archive as `SpirialisHelper.zip` in the original installation's `Mods` directory.

## Placement

```text
Workspace/
  Shared/
  Tools/
  Mods/
    SpirialisHelper/                 # this repository

Celeste/                    # your original game installation
  Celeste.dll
  FNA.dll
  Mods/
    SpirialisHelper.zip
```

Other required Mod archives stay together in the original installation's `Mods`
directory.

## Build

From the workspace directory, use the host options in the
[Tools README][tools-readme]. For example, for Godot:

```powershell
pwsh ./Tools/Prepare.ps1 `
  -CelesteDirectory '/path/to/Celeste' `
  -AudioBankDirectory '/path/to/Desktop' `
  -Targets Godot `
  -IncludeHelpers
```

Preparation verifies the supported inputs, builds dependencies and creates the
runtime package at `Content/Celeste/Mods/SpirialisHelper.zip`. Generated source, tools and
intermediate build files remain under the workspace's ignored `artifacts/`
directory.

## License

See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md). Original game files, Mod
archives and locally generated packages are not included in this repository.

[workspace-readme]: https://github.com/CelesteResearch/Workspace/blob/main/README.md
[tools-readme]: https://github.com/CelesteResearch/Tools/blob/main/README.md
