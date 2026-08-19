# Release/

> 受控发布态：每版本冻结快照，hw/fw/mech 对齐锚点。

## 目录结构

```text
Release/vX.Y.Z/
├── firmware_vX.Y.Z.bin / .hex
├── firmware_vX.Y.Z.sha256   固件校验值
├── bootloader_vX.Y.Z.bin
├── release_note.md
└── production_package.zip   量产快照
```

## 规则

- tag = 目录 = 版本号；
- release_note 列三方版本 + 固件 SHA256；固件由 CI 构建并记录 commit；
- 根 CHANGELOG.md = 项目级历史；release_note = 单版本明细；
- 固件/量产包走 LFS；量产烧录只从此目录取；
- 产测规范在 Test/Production_Test/，打包时冻结副本。
