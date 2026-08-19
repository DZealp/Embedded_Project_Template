# STRUCTURE.md — 目录结构与规则

> 根目录结构与顶层规则。总览见 [README.md](README.md)。

## 1. 文档分层

| 层级 | 位置 | 内容 |
|------|------|------|
| L1 宏观 | 根 STRUCTURE.md | 顶层职责、边界判据 |
| L2 目录 | `<目录>/STRUCTURE.md` | 目录内部结构（子目录在此介绍） |

规则：上层只承诺本层结构；L1/L2 目录与 STRUCTURE.md 一一对应，**子目录不单独建文档**、在所属 L2 文档中介绍；L1 保持精简——性质相近的顶层目录并入其他目录（结构→Hardware/Mechanical/、认证→Docs/Certification/、脚本→Tools/Scripts/）。

## 2. 目录结构

```text
Embedded_Project_Template/
├── README.md      项目总览
├── STRUCTURE.md   目录结构与规则（本文件）
├── Hardware/   硬件+结构设计（设计态）
├── Firmware/   固件（源码工程，结构自定）
├── Software/   上位机/移动端/云端
├── Test/       系统级测试与报告（含产测规范）
├── Docs/       项目文档+认证
├── Release/    版本发布归档（受控发布态）
├── Tools/      工具与脚本
├── .gitignore          忽略规则
├── .gitattributes      LFS/行尾规则
├── .gitmodules         子模块
├── CODEOWNERS          审查人映射（可选）
├── CHANGELOG.md        变更历史（可选）
├── .github/workflows/   CI 配置（可选）
└── LICENSE
```

## 3. 导航

| 目录 | 职责 | 细化文档 |
|------|------|----------|
| Hardware/ | 硬件+结构设计 | [Hardware/STRUCTURE.md](Hardware/STRUCTURE.md) |
| Firmware/ | 固件（结构自定） | [Firmware/STRUCTURE.md](Firmware/STRUCTURE.md) |
| Software/ | 上位机/移动端/云端 | [Software/STRUCTURE.md](Software/STRUCTURE.md) |
| Test/ | 测试与产测规范 | [Test/STRUCTURE.md](Test/STRUCTURE.md) |
| Docs/ | 文档+认证 | [Docs/STRUCTURE.md](Docs/STRUCTURE.md) |
| Release/ | 受控发布 | [Release/STRUCTURE.md](Release/STRUCTURE.md) |
| Tools/ | 工具与脚本 | [Tools/STRUCTURE.md](Tools/STRUCTURE.md) |

## 4. 边界判据

> 三对判据用于裁决"文件该放哪个目录"：先按生命周期状态，再按验证/合规属性，最后按自研/第三方归属。

### 4.1 设计态 vs 受控发布态

- **设计态**：研发过程中持续变更的源文件与导出物 → `Hardware/`（含 `Hardware/Mechanical/`）；
- **受控发布态**：每版本冻结、只增不改的发布快照 → `Release/vX.Y.Z/`；
- **工厂过程文件**（产线 SOP/IQC）→ 不入库，由工厂自行管理；
- **工程师 → 工厂的交接物** = 设计文件（`Hardware/`）+ 固件（`Release/`）+ 产测规范（`Test/Production_Test/`）；
- 发布快照 `production_package.zip` 冻结、可追溯，与 git tag 一一对应。

### 4.2 研发验证 vs 合规认证

- **研发验证**：内部验证、预测试报告 → `Test/Test_Report/`；
- **合规认证**：官方证书与正式报告 → `Docs/Certification/`；
- 两者由 `Certification_Tracker.xlsx` 关联，保证"内部预扫 → 官方认证"链路可追溯。

### 4.3 自研 vs 第三方

- **自研产品级工具/应用** → `Software/`；
- **自研辅助脚本** → `Tools/Scripts/`；
- **第三方工具配置/脚本** → `Tools/`（安装包不入库）。

## 5. 版本对齐

- tag = Release/vX.Y.Z = hw/fw/mech 三方对齐锚点；
- Hardware/、Hardware/Mechanical/ 的 Changelog 注明对应固件 tag；
- release_note 列三方版本 + 固件 SHA256。

## 6. 工程化

- 可选工程化项：.github/workflows/（CI）、CODEOWNERS、CHANGELOG.md 均可选，单人/小团队可暂不建立，按需引入；
- CODEOWNERS 按目录映射审查人；
- 根级文件归属：.gitattributes/.gitmodules 必须根目录；.gitignore 根目录为默认、子目录可按需局部覆盖；CHANGELOG.md 项目级历史在根；.editorconfig/.clang-format/Makefile 不入根，由源码工程自定；
- 构建相关路径 ASCII 无空格；纯文档 YYYYMMDD_ 前缀；
- 大二进制走 LFS；空目录 .gitkeep；源码 LF 行尾；
- vendor/生成代码只读，修改走重新生成/子模块升级。
