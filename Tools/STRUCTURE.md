# Tools/

> 自研辅助脚本 + 第三方工具配置。不提交安装包。

## 目录结构

```text
Tools/
├── Scripts/      自研脚本
│   ├── build.sh          构建入口
│   ├── flash.sh          烧录
│   ├── gen_version.py    版本号生成
│   ├── pack_firmware.py  固件打包
│   └── ci/               CI 调用的 helper 脚本
├── JLink/        J-Link 配置
├── Serial/       串口调试工具配置
└── OTA_Tool/     第三方 OTA 工具配置（自研则归 Software/PC_App/）
```

## 规则

- 产品级工具 → Software/；辅助脚本与第三方配置 → 本目录；
- CI 配置在 .github/workflows/，不在本目录；
- 不提交安装包；脚本幂等、参数化，记录工具版本。
