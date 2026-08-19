# Test/

> 系统级测试与报告。单测随源码（Firmware/SourceCode/、Software/ 各工程）；产测规范在本目录。

## 目录结构

```text
Test/
├── Integration_Test/   集成/HIL 测试
├── Production_Test/    产测规范（面向工厂）
│   ├── flash_guide.md         烧录指引
│   ├── functional_test.md     功能测试规范
│   ├── aging_spec.md          老化规范
│   └── test_procedure/        （可选）产测程序
├── Test_Report/        内部验证/预测试报告
├── Test_Plan/          测试计划
└── Test_Fixture/       测试治具（独立子项目）
```

## 规则

- 内部报告归 Test_Report/；官方认证归 Docs/Certification/，由 Tracker 关联；
- Production_Test/ 面向量产执行，按产线可执行性编写（步骤+判据）；打包时冻结规范副本入 Release/vX.Y.Z/production_package.zip；产测固件按 Test_Fixture/ 规则管理；
- 研发验证在 Integration_Test/ 与单测；
- 测试不参与量产编译。
