# 源与校验

所有上游来源均公开可验证，哈希与 `recipes/<版本>/PKGBUILD` 的 `b2sums` 一致。

## 内核源码 tarball

来自 `CachyOS/linux` GitHub Releases，URL 模板：

```
https://github.com/CachyOS/linux/releases/download/cachyos-<ver>-1/cachyos-<ver>-1.tar.gz
```

| 版本 | 文件 | b2sum (blake2b-512) |
|---|---|---|
| 7.2.6 | cachyos-7.2.6-1.tar.gz | `ed4476f3d7fcd852ed7ce14de2652d706d456e0e3d0002fa22feb5ba5a91376a1e2409ed765dbdf671c28222bac095b93be64aae9673bdec8bc603378d31220a` |
| 7.2.7 | cachyos-7.2.7-1.tar.gz | `19720409be3c7a5f2ccfa447c9eddb4fafd248d196e042283e5d0c265591bfa36bfe8ab7ccc549d987537d66fb2d6222ce6ae0921a12910c6c0cde2303f32baf` |
| 7.2.8 | cachyos-7.2.8-1.tar.gz | `e9c1784d45b95872cee8a993c96659dda4174b1e42097757dcbada2f1041776a67009caefe0ed0b5af2c3d9811d0cb8f72c67b988f0aef1673ed6d38b901154b` |

## 内核配置种子

`recipes/<版本>/config`，三版一致：

```
21343697f5f1647aadbdec8a4aa477b10622e5ae04fa07fcf6f9bab67dece7180872676bdc49a90de5d273c2c13127c5812a7ca67dbd9edce3e26e8c38d358d1
```

## 内核补丁

| 文件 | 上游 URL | b2sum |
|---|---|---|
| dkms-clang.patch | `https://raw.githubusercontent.com/cachyos/kernel-patches/master/7.2/misc/dkms-clang.patch` | `c992567bd7dd8553432be496ffa1c17e2f5ebe9c7edb51945cf977e1b742dd6517c210d8843bb82744ca705efd07f8027cd7dde41b50215ebd707a34aa81462e` |
| 0001-bore-cachy.patch | `https://raw.githubusercontent.com/cachyos/kernel-patches/master/7.2/sched/0001-bore-cachy.patch` | `03b6d236610ae00db9395819aa7578860f45ce10839fbdcee80fb8e9e9c8810896d20680c63e43c416ae23b371efd737bc0a14831e1f7d8111578c1f65bda68f` |

> PKGBUILD 中这些 URL 带 `https://ghfast.top/` 镜像前缀（便于国内拉取），b2sum 校验一致。
