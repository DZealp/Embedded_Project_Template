# Embedded_Project_Template

**Embedded Project Directory Template** —— 面向嵌入式产品全生命周期的目录结构模板：硬件/结构、固件、上位机/移动端软件、测试、文档、认证、发布、工具一站式布局，配套文档分层体系与子仓库管理规范。

A directory structure template for the full lifecycle of embedded products, with layered documentation and submodule management conventions.

## 特性

- **软硬件同仓管理**：硬件设计、结构、固件、软件同仓布局，git tag 作为软硬件版本对齐锚点（`Release/vX.Y.Z`）
- **文档分层（L1/L2）**：根 `STRUCTURE.md` 定义顶层职责与边界判据，各目录 `STRUCTURE.md` 细化内部结构；子目录不单独建文档，在所属 L2 文档中介绍
- **目录即边界**：每个顶层目录职责单一，天然适配 CODEOWNERS 审查人映射与 CI 目录级触发
- **子模块架构**：固件/软件工程作为独立仓库（submodule）挂载，主仓冻结指针保证版本可追溯（见 [Submodule_Management.md](Docs/Process/Submodule_Management.md)）
- **版本控制友好**：Git LFS（PCB/Gerber/STEP/固件包）、.gitignore、行尾统一、目录深度控制
- **生产可交接**：产测规范（`Test/Production_Test/`）面向工厂编写，每版本受控发布快照（`Release/vX.Y.Z/production_package.zip`）冻结可追溯
- **工程化配套**：CI 配置位置、命名规范、生成 vs 手改纪律、根级文件归属规则

## 目录结构

```text
Embedded_Project_Template/
├── README.md      项目总览
├── STRUCTURE.md   目录结构与规则（L1 宏观）
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

## 快速开始

1. **克隆模板**：`git clone https://github.com/<your-name>/Embedded_Project_Template.git my_project`
2. **按需裁剪**：删除用不到的占位目录（如 `Software/Server/`），重命名占位工程目录（`Firmware/SourceCode/`、`Software/PC_Software/` 等）
3. **初始化代码工程**：固件/软件内部结构由各工程自定；需独立版本节奏的工程拆为子仓库（见 [Submodule_Management.md](Docs/Process/Submodule_Management.md)）
4. **落地工程化文件**：配置 `.gitattributes`（LFS 规则）、`.gitignore`；`CODEOWNERS`、CI 按需引入
5. **按文档分层细化**：逐目录补充 `STRUCTURE.md` 中的实际内容与规则

## 文档导航

| 文档 | 内容 |
|------|------|
| [STRUCTURE.md](STRUCTURE.md) | 目录结构与规则（L1 宏观：分层约定、边界判据、版本对齐、工程化） |
| `<目录>/STRUCTURE.md` | 各目录内部结构与规则（L2，共 7 份） |
| [Docs/Process/Submodule_Management.md](Docs/Process/Submodule_Management.md) | 子仓库（Submodule）管理规范 |
| `Docs/` | 项目文档布局：需求 → 设计 → 用户 → 流程，认证归档 |

## 目录职责速览

| 目录 | 职责 |
|------|------|
| `Hardware/` | 硬件+结构设计（设计态），设计文件唯一维护点 |
| `Firmware/` | 固件源码工程（占位，工程自定结构） |
| `Software/` | 自研电脑端/移动端/云端软件工程 |
| `Test/` | 系统级测试与报告（含产测规范） |
| `Docs/` | 项目文档+认证归档 |
| `Release/` | 受控发布快照（软硬件版本对齐锚点） |
| `Tools/` | 辅助脚本与第三方工具配置 |

## License

[MIT License](LICENSE)

