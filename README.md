# KBkernel-cachy

自编译 Linux 内核（CachyOS `linux-cachyos` 基座 + 本地定制）的**配方与发布**仓库。

- **产物**（`*.pkg.tar.zst`）与**对应源码**随每次构建发布到 [Releases](../../releases)
- **构建配方**按版本收录于 `recipes/`

## 基座与来源

| 项 | 来源 |
|---|---|
| 内核源码 tarball | `CachyOS/linux` releases（`cachyos-<ver>-1.tar.gz`，逐版本 b2sum 固定） |
| 内核补丁 | `cachyos/kernel-patches` |
| 配方上游 | `CachyOS/linux-cachyos` |

确切 URL 与哈希见 [SOURCES.md](SOURCES.md)。

## 定制

- CachyOS 调度器 **BORE**（`SCHED_BORE`）
- **ThinLTO**（`clang` + `ld.lld`）
- 目标微架构 **x86-64-v3**（`generic_v3`）
- 构建者标识 `user@host` 与真实编译时间戳
- 关闭 **Intel 无线 LAR**：补丁补回 iwlwifi `lar_disable` 参数 + 包内 `/usr/lib/modprobe.d/iwlwifi-lar.conf`

> 历史配方 7.2.6 – 7.2.8 另含 **5 级页表关闭（LA57）**，该配置已在后续版本移除。

## 目录

```
recipes/<版本>/
├─ PKGBUILD    Arch makepkg 构建配方
├─ config      内核配置种子（哈希与 PKGBUILD 的 b2sums 一致）
└─ .SRCINFO    源信息（makepkg --printsrcinfo）
```

## 构建

```bash
cd recipes/<版本>
makepkg -s --noconfirm
```

产物：`linux-kbkernel-cachy-<版本>-<pkgrel>-x86_64.pkg.tar.zst`（及 `-headers`）。

> 本仓库仅提供配方；内核源码来自上述公开上游，配方中的 `source` / `b2sums` 锁定了确切来源与校验值。

## 许可

内核与配方衍生自 GNU General Public License v2（见 [LICENSE](LICENSE)）。分发二进制时随附的对应源码 = 本仓库配方 + 公开上游源码。
