# Hardware/

> 硬件+结构设计（设计态）。设计文件唯一维护点；量产快照由 Release/ 打包。

## 目录结构

```text
Hardware/
├── Schematic/         原理图（按板卡）
├── PCB/
│   ├── Gerber/<vX.Y_YYYYMMDD>/   Gerber/钻带按版本归档
│   └── SMT/<vX.Y>/              贴片导出物随 PCB 版本
├── Lib/               SchLib/、PcbLib/（器件级 3D 在 PcbLib/3D/）
├── BOM/               物料清单
├── 3D/                板卡级导出（STEP/IDF），供结构装配
├── Review/            DFM/DFT、设计评审记录（可选）
├── Mechanical/        结构设计（外壳/散热/装配）
│   ├── Enclosure/     外壳件：原生 CAD 与 STEP 同目录（LFS）
│   ├── Heatsink/      散热件（.gitkeep）
│   ├── Drawing/       结构图纸
│   ├── Assembly/      装配指导（设计侧）
│   └── Mechanical_Changelog.md
└── Hardware_Changelog.md
```

## 规则

- 导出物按版本归档，只增不改，禁止覆盖历史；
- PcbDoc/STEP/PDF 走 LFS；
- Lib 变更记录影响面；
- 板卡 STEP 供 Mechanical/ 装配；器件级 3D 归 PcbLib/3D/；
- 改版与固件以 tag 对齐（见[根 STRUCTURE.md 第 5 节](../STRUCTURE.md#5-版本对齐)）；
- Mechanical/：原生 CAD 与 STEP 同目录入库（LFS）；Assembly/ 为设计侧指导，工厂 SOP 不入库；Mechanical_Changelog 注明硬件/固件版本；装配快照由 Release/ 打包。
