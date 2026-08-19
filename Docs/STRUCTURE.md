# Docs/

> 项目文档：需求→设计→用户→流程；认证归档并入本目录。

## 目录结构

```text
Docs/
├── Requirement/   需求
├── Design/        设计
│   ├── System/    系统级（软硬件共同评审）
│   ├── Hardware/  硬件
│   ├── Software/  软件
│   └── Protocol/  接口协议
├── User_Manual/   用户手册（交付物）
├── Process/       流程
├── Management/    管理类归档
│   ├── Risk_Register.xlsx   风险登记册
│   ├── Decision_Log.md      决策记录
│   └── Review_Records/      评审记录
├── Certification/ 认证与合规（官方证书+正式报告）
│   ├── FCC/  CE/  CCC/  RoHS/  UL/   （.gitkeep）
│   └── Certification_Tracker.xlsx   报告 ↔ 固件/硬件版本
├── Meeting/       会议纪要
├── Training/      培训资料
├── Glossary.md    术语表
└── README.md      文档导航 + 交付件清单
```

## 规则

- 共同评审文档 → Design/System/；单方评审 → Design/Hardware/ 或 Design/Software/；
- PDF 为发布件，源文件（docx 等）同目录同版本存放；
- 官方认证报告归 Certification/，内部报告在 Test/Test_Report/，由 Tracker 关联；
- 证书 PDF 走 LFS。
