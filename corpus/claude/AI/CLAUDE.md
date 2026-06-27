# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

个人知识管理仓库，包含技术、生活、健康、财务、职业、法律和旅游等内容。

**项目特定说明**：
- 主语言为中文（简体），文档和注释均使用中文
- 主要技术项目位于 `01-技术/硬件开发/3D打印机/AI工具/ai-3d-generator/`

---

## 目录结构

```
.
├── 01-工作/                    # 工作相关内容
│   ├── 工作汇总/               # 工作总结、汇总文档
│   ├── 招聘面试/               # 面试题库、流程文档
│   ├── 创意灵感/               # 创意和想法记录
│   ├── 内容审核/               # 内容审核相关
│   ├── 团队管理/               # 团队管理工具和文档
│   ├── 英语学习/               # 英语学习资料
│   ├── Kiro项目/               # Kiro AI IDE研究
│   └── 自媒体/                 # 博主和自媒体相关
│
├── 01-技术/                    # 技术相关内容
│   ├── AI工具/                 # AI工具使用指南
│   │   ├── 大语言模型研究/      # L1-LLM内容
│   │   ├── AI应用开发/         # L2-Application内容
│   │   ├── AI工作流自动化/     # L3-WorkFlow内容
│   │   ├── 智能编程助手/       # L4-Agent内容
│   │   ├── AI管理提示词/       # AI管理提示词
│   │   ├── 深度研究/           # 算法和数据结构研究（英文命名）
│   │   └── 视频生成/Sora/      # Sora视频生成
│   ├── 电脑网络/              # 网络配置、IPTV等
│   ├── 软件工具/              # MCP、AI工具汇总
│   │   ├── MCP/               # MCP协议研究
│   │   │   ├── Python实现/    # Python MCP实现
│   │   │   └── JavaScript实现/ # JavaScript MCP实现
│   │   └── 工具/              # 其他工具
│   ├── 硬件开发/              # 硬件开发项目
│   │   └── 3D打印机/          # 3D打印相关（包含AI 3D生成器）
│   │       └── AI技术知识库/  # 3D模型技术知识
│   ├── 技术实践/              # TECH内容
│   ├── 架构设计/              # TechArchAI内容
│   ├── 开发工具/              # ClaudeCode、Cursor等
│   │   ├── ClaudeCode/        # Claude Code相关
│   │   ├── Cursor/            # Cursor编辑器
│   │   ├── CodeBuddy/         # CodeBuddy工具
│   │   └── Trae/              # Trae工具
│   ├── 跨领域研究/            # 跨领域技术研究
│   ├── 未来研究/              # Future内容
│   ├── 设计工具/              # Figma等设计工具
│   └── 内容创作/              # Blog、PPT等
│
├── 02-生活/                   # 生活相关
│   ├── 宠物/                  # 猫、狗饲养记录
│   │   └── 狗/                # 狗相关内容
│   ├── 购物/                  # 购物相关
│   ├── 家居装修/              # 装修知识、暖气片等
│   ├── 交通出行/              # 汽车、摩托车、通勤方案
│   ├── 生活习惯管理/          # 生活习惯相关
│   ├── 电脑桌面/              # Desktop内容
│   ├── 天气/                  # 天气API、定时任务
│   └── 旅游/                  # 旅游指南
│       ├── 日本/              # 日本旅游准备、签证
│       ├── 澳门/              # 澳门旅游记录
│       ├── 越南/              # 越南旅游规划
│       ├── 旅行记录/          # Trip内容
│       └── 通用指南/          # 签证、外币代取等
│
├── 03-健康/                   # 健康记录
│   ├── 健康汇总/              # 健康相关汇总
│   ├── 备孕计划/              # 备孕相关文档
│   ├── 医疗健康/              # SLE、疫苗等健康记录
│   ├── 生病/                  # 生病相关记录
│   ├── 宠物医疗/              # 宠物医疗记录
│   └── 行政事务/              # 行政事务相关
│
├── 03-自动化/                 # 自动化脚本
│   ├── 邮件摘要/              # 邮件自动摘要
│   └── 语音记录/              # 会议总结、日记、通勤日志
│
├── 04-财务/                   # 公积金、保险规划
├── 04-Moltbook平台监控/       # Moltbook平台监控
├── 05-职业/                   # 职业发展分析、公司调研、校友会
├── 06-法律/                   # 法律案件、合同模板、维权工具
├── 07-宠物管理网站/           # 宠物管理网站项目
├── README.md                  # 仓库总说明
├── 文件存储规则.md            # 文件组织规范
└── CLAUDE.md                  # 本文件
```

---

## 编号系统

| 编号 | 类别 | 说明 |
|------|------|------|
| 01 | 工作/技术 | 两个01开头，分别用于工作和技术 |
| 02 | 生活 | 生活相关内容 |
| 03 | 健康/自动化 | 两个03开头 |
| 04 | 财务/Moltbook | 两个04开头 |
| 05 | 职业 | 职业发展 |
| 06 | 法律 | 法律事务 |
| 07 | 宠物管理网站 | 独立项目 |

---

## 命名规范

### 技术目录
- 统一使用英文命名
- 统一使用小写字母
- 避免使用空格和特殊字符

### 生活目录
- 使用中文命名
- 避免使用"合并"等临时后缀

### 通用规则
- 不使用"合并"、"临时"等后缀
- 目录名称应清晰反映内容
- 避免过深的嵌套层级

---

## AI 3D模型生成器

**位置**: `01-技术/硬件开发/3D打印机/AI工具/ai-3d-generator/`

### 常用命令

```bash
# 进入项目目录
cd "01-技术/硬件开发/3D打印机/AI工具/ai-3d-generator"

# 安装依赖
pip install -r requirements.txt

# 启动应用（开发模式）
python run.py

# 启动应用（生产模式）
uvicorn main:app --host 0.0.0.0 --port 8000

# 使用 Python 直接启动
python main.py

# 运行测试（如果有）
pytest tests/
```

### 配置文件

- **环境变量**: 复制 `.env.example` 为 `.env` 并修改配置
- **主要配置项**（在 `.env` 或 `config.py` 中）:
  - `PRINTER_MAX_X/Y/Z`: 打印机尺寸（默认 256mm）
  - `USE_GPU`: 是否使用GPU加速
  - `DATABASE_URL`: SQLite数据库路径
  - `LOG_LEVEL`: 日志级别

### 架构概览

```
main.py                    # FastAPI 应用入口
├── config.py              # 配置管理（打印机规格等）
├── logger.py              # 日志模块
├── requirements.txt       # Python依赖
├── api/                   # API 路由
│   └── upload.py         # 图像上传API
├── modules/              # 核心功能模块
│   ├── ai_inference.py       # AI推理引擎（图像分析、深度估计、点云生成）
│   ├── model_optimizer.py    # 3D打印优化器（缩放、支撑、修复）
│   ├── model_generator.py    # 3D模型生成（点云转网格）
│   ├── image_processor.py    # 图像预处理
│   ├── file_converter.py     # 文件格式转换（STL/3MF）
│   └── image_upload.py       # 图像上传模块
├── database/             # 数据库模型
│   ├── models.py         # SQLAlchemy模型定义
│   └── database.py       # 数据库初始化
└── tests/                # 单元测试
```

### 数据流

```
图像上传 → ImagePreprocessor → AIInferenceEngine → PointCloud
                                                  ↓
                                          ModelGenerator → Mesh
                                                  ↓
                                          ModelOptimizer → 打印优化
                                                  ↓
                                          FileConverter → .3mf/.stl
```

### 关键模块说明

1. **AIInferenceEngine** (`modules/ai_inference.py`):
   - 图像分析、物体检测、深度估计
   - 从场景描述生成点云数据
   - 支持多种3D形状模板（立方体、球体、圆柱等）

2. **ModelOptimizer** (`modules/model_optimizer.py`):
   - 针对拓竹P1SC打印机规格优化模型
   - 自动缩放、添加支撑、修复网格缺陷
   - 优化打印方向

3. **配置系统** (`config.py`):
   - 打印机规格配置（256×256×256mm）
   - 文件存储路径
   - AI模型设置

### 打印机规格（拓竹 P1SC）

- 打印体积: 256×256×256 mm³
- 喷嘴: 0.4mm 不锈钢（默认）
- 支持材料: PLA, PETG, TPU, ABS, ASA, PVA, PET
- 不推荐: 碳纤维/玻璃纤维增强材料

---

## PowerShell 脚本

**位置**: `01-技术/硬件开发/3D打印机/个人项目/Scripts/`

### 模型整理脚本

```powershell
# 运行模型整理脚本
.\Scripts\organize_models.ps1 -SourceDirectory "开源模型" -TargetDirectory "开源模型-纯享"

# 查看 PowerShell 脚本编码（必须是 UTF-8 with BOM）
Get-Content .\Scripts\organize_models.ps1 | Format-Hex
```

### PowerShell 脚本规范

- **编码**: 必须使用 `UTF-8 with BOM`
- **核心 Cmdlet**: `Get-ChildItem`, `Move-Item`, `Rename-Item`, `New-Item`, `Remove-Item`, `Expand-Archive`
- **路径处理**: 优先使用 `$PSScriptRoot` 构建相对路径
- **设计原则**: 非交互式，避免 `Read-Host`

---

## 文件组织规范

### 3D模型命名

`开源模型-纯享/` 中的文件夹命名格式：
```
来源-作者-模型描述[-部件名]
```

示例：`makerworld-JohnDoe-Dragon-Bust-Head`

### 文件格式优先级

`.3mf` > `.stl`（.3mf 包含颜色信息和多部件组合）

---

## 依赖要求

### Python 版本

- Python 3.8 或更高版本

### 主要依赖

```
fastapi==0.104.1
uvicorn==0.24.0
torch==2.1.0
open3d==0.18.0
trimesh==4.0.5
transformers==4.35.2
sqlalchemy==2.0.23
```

---

## 沟通语言

**始终使用简体中文进行交流。**

---

## 关键设计决策

1. **打印机为中心**: 所有决策都考虑 P1SC 的能力和限制
2. **自动化优先**: 使用 PowerShell 脚本处理重复性任务
3. **质量优先**: `开源模型-纯享/` 必须是经过验证可打印的高质量文件
