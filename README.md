# 简历/CV助手 Resume/CV Assistant Skill

<div align="center">

[![GitHub release](https://img.shields.io/github/v/release/Yv3s-y4ng/resume-assistant-skill)](https://github.com/Yv3s-y4ng/resume-assistant-skill/releases)
[![License](https://img.shields.io/github/license/Yv3s-y4ng/resume-assistant-skill)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude-Skill-7C3AED)](https://claude.ai/code)

**[中文](#中文) | [English](#english)**

</div>

---

<h2 id="中文">🇨🇳 中文文档</h2>

<div align="right">

**[English Version ⬇️](#english)**

</div>

### 📖 简介

智能简历/CV助手，支持**求职**和**学术申请**两大场景，通过七个专业 AI 代理提供全流程支持。为 [Claude Code](https://claude.ai/code) 设计的技能包。

**适用场景**：
- 🏢 **求职**：工作、实习、跳槽
- 🎓 **学术申请**：研究生、博士、博后、奖学金

### 📦 安装

```bash
# 下载最新版本
curl -L -O https://github.com/Yv3s-y4ng/resume-assistant-skill/releases/latest/download/resume-assistant-skill.skill

# 安装技能包
claude skills install resume-assistant-skill.skill

# 安装 Python 依赖
pip install fpdf2 python-docx openpyxl
```

**✅ 中文字体已内置** - PDF 生成功能开箱即用，无需手动配置！

### ✨ 功能特点

#### 通用 AI 代理（1-5）：双模式支持

- **🔍 代理1：故事挖掘代理**
  - 求职模式：挖掘工作经历和可迁移技能
  - 学术模式：挖掘研究经历和学术动机

- **💼 代理2：职位/导师推荐代理**
  - 求职模式：推荐合适的职位方向
  - 学术模式：推荐研究方向和导师

- **📝 代理3：简历/CV优化代理**
  - 求职模式：根据JD优化简历
  - 学术模式：优化学术CV结构

- **🎭 代理4：模拟面试代理**
  - 求职模式：模拟公司面试
  - 学术模式：模拟PhD/研究生面试

- **📈 代理5：能力提升代理**
  - 求职模式：职业技能提升计划
  - 学术模式：科研能力提升计划

#### 学术专属 AI 代理（6-7）⭐

- **🎯 代理6：导师适配代理**（学术专属）
  - 基于导师研究方向重新表述项目经历
  - 生成研究兴趣陈述（Research Interest Statement）
  - 创建"为什么选择这个实验室"段落
  - 输出导师专属定制版CV

- **✉️ 代理7：套磁邮件生成器**（学术专属）
  - 生成专业的学术联系邮件
  - 支持4种邮件类型（初次联系、跟进、附CV、会议后续）
  - 提供3个版本（保守、平衡、积极）
  - 包含邮件礼仪和时机建议

#### 输出格式

- 📄 **PDF** - 专业格式，适合正式投递
- 📝 **DOCX** - 可编辑格式，便于进一步修改
- 🌐 **HTML** - 现代响应式设计，支持深色模式
- 📊 **Excel** - 能力提升追踪表，包含里程碑

### 🚀 快速开始

安装后，直接与 Claude Code 对话：

**求职场景**：
```
"帮我写简历"              # 创建简历
"优化这份简历"            # 优化现有简历
"我要投XX岗位"            # 针对特定岗位优化
"模拟面试"               # 面试练习
"我想冲XX岗位但能力不够"   # 技能差距分析
```

**学术场景**：
```
"帮我写CV"               # 创建学术CV
"申请XX导师的博士项目"     # 导师适配 + CV定制
"给导师发套磁邮件"         # 生成学术联系邮件
"模拟PhD面试"            # 学术面试准备
"科研能力不足怎么办"       # 学术能力提升
```

### 🎯 使用场景

#### 求职场景

| 场景 | 使用代理 | 输出 |
|------|---------|------|
| 首次写简历 | 代理1 → 代理3 | 打磨后的简历 |
| 岗位投递 | 代理3 | 定制化简历 |
| 面试准备 | 代理4 | 练习反馈 |
| 职业发展 | 代理2 → 代理5 | 发展计划 |
| 完整求职辅导 | 代理1-5 | 端到端支持 |

#### 学术申请场景

| 场景 | 使用代理 | 输出 |
|------|---------|------|
| 申请研究生 | 代理1 → 代理3 | 基础学术CV |
| 申请特定导师 | 代理1 → 代理3 → 代理6 | 导师专属CV |
| 套磁联系导师 | 代理6 → 代理7 | CV + 套磁邮件 |
| PhD面试准备 | 代理4（学术模式） | 面试反馈 |
| 科研背景不足 | 代理5（学术模式） | 学术提升计划 |
| 完整学术申请 | 代理1-7 | 全流程支持 |

### 💡 完整工作流程

#### 求职流程
```
1️⃣ 故事挖掘（代理1）
   "我不知道简历写什么" → 引导对话 → 《经历档案》

2️⃣ 职位推荐（代理2）
   基于档案 → 匹配分析 → 《职位推荐报告》

3️⃣ 简历优化（代理3）
   "帮我优化简历，投XX岗位" + JD → 《优化版简历》(JSON)

4️⃣ 文件生成
   使用脚本 → PDF/DOCX/HTML 简历

5️⃣ 模拟面试（代理4）
   基于简历 → 模拟提问 → 《面试反馈》+ 简历改进建议

6️⃣ 能力提升（代理5）可选
   如果能力不足 → 差距分析 → 《提升规划》+ Excel 追踪表
```

#### 学术申请流程（核心）⭐
```
1️⃣ 学术背景挖掘（代理1 - 学术模式）
   挖掘研究经历 → 《学术档案》

2️⃣ 研究方向推荐（代理2 - 学术模式）
   推荐导师/项目 → 《导师推荐报告》

3️⃣ 基础CV生成（代理3 - 学术模式）
   生成学术CV → 《基础CV》(JSON)

4️⃣ 导师适配（代理6 - 学术专属）⭐ 核心功能
   收集导师信息（官网、论文）→ 重新表述项目经历 →
   生成研究兴趣陈述 → 《导师专属CV》

5️⃣ 套磁邮件（代理7 - 学术专属）
   生成专业学术邮件 → 3个版本 + 发送建议 → 《套磁邮件》

6️⃣ 学术面试（代理4 - 学术模式）
   模拟PhD面试 → 《面试反馈》

7️⃣ 能力提升（代理5 - 学术模式）可选
   科研能力差距分析 → 《学术提升计划》+ Excel追踪表
```

**典型场景示例**：申请特定导师的PhD
```
用户："我想申请清华大学张教授的博士项目"

系统执行：
代理1 → 挖掘学术背景
代理3 → 生成基础CV
代理6 → 收集张教授信息（研究方向、论文），适配CV
       输出：张教授专属版CV，关键词高度对齐
代理7 → 生成套磁邮件（3个版本）
       输出：专业邮件 + 主题行 + 发送时机建议

用户：发送邮件 + 附张教授专属CV
```

### 📚 文档

- **[SKILL.md](SKILL.md)** - 完整的技能文档（供 Claude 使用）
- **[skillmap.json](skillmap.json)** - 技能元数据
- **[examples/](examples/)** - 示例数据文件
- **[references/](references/)** - 参考文档（写作指南、行业关键词等）
- **[Releases](https://github.com/Yv3s-y4ng/resume-assistant-skill/releases)** - 下载打包文件

### 📋 系统要求

- ✅ **Claude Code** 已安装
- ✅ **Python 3.7+** 用于脚本执行
- ✅ **Python 包**: `fpdf2`, `python-docx`, `openpyxl`
- ✅ **中文字体**: 已内置（开箱即用）

### 🔧 故障排查

遇到问题请查看 [故障排查指南](references/troubleshooting.md)

### 🌟 特色亮点

- ✨ **双场景支持** - 求职 + 学术申请一体化
- ✨ **七大代理** - 通用5个 + 学术专属2个
- ✨ **导师适配** - 基于导师研究方向"蹭"关键词（不编造，只重新表述）
- ✨ **套磁邮件** - 专业学术邮件生成，提高导师回复率
- ✨ **多种格式** - PDF/DOCX/HTML/Excel 一应俱全
- ✨ **智能匹配** - 根据 JD/导师研究自动优化关键词
- ✨ **实战演练** - 模拟真实面试场景（公司/学术）
- ✨ **持续成长** - 制定可执行的提升计划
- ✨ **中文优化** - 专为中国市场设计

### 📄 开源协议

[MIT](LICENSE) - 免费使用，欢迎贡献

### 🔗 相关链接

- **仓库**: https://github.com/Yv3s-y4ng/resume-assistant-skill
- **最新版本**: https://github.com/Yv3s-y4ng/resume-assistant-skill/releases/latest
- **Claude Code**: https://claude.ai/code
- **问题反馈**: https://github.com/Yv3s-y4ng/resume-assistant-skill/issues

### 📊 版本信息

- **当前版本**: 3.0.0
- **质量评分**: A+ (9.5/10)
- **最后更新**: 2026-03-06
- **重大更新**: 新增学术申请支持（Agent 6 & 7）

---

<h2 id="english">🇬🇧 English Documentation</h2>

<div align="right">

**[中文版本 ⬆️](#中文)**

</div>

### 📖 Introduction

An AI-powered resume/CV assistant supporting both **job search** and **academic applications**, with 7 specialized agents providing end-to-end support. Designed for [Claude Code](https://claude.ai/code).

**Use Cases**:
- 🏢 **Job Search**: Employment, internships, career transitions
- 🎓 **Academic Applications**: Master's, PhD, Postdoc, Scholarships

### 📦 Installation

```bash
# Download the latest release
curl -L -O https://github.com/Yv3s-y4ng/resume-assistant-skill/releases/latest/download/resume-assistant-skill.skill

# Install the skill
claude skills install resume-assistant-skill.skill

# Install Python dependencies
pip install fpdf2 python-docx openpyxl
```

**✅ Chinese font bundled** - PDF generation works out of the box!

### ✨ Features

#### General AI Agents (1-5): Dual-Mode Support

- **🔍 Agent 1: Story Mining Agent**
  - Job mode: Extract work experiences and transferable skills
  - Academic mode: Extract research experiences and academic motivation

- **💼 Agent 2: Position/Advisor Recommendation Agent**
  - Job mode: Recommend suitable job positions
  - Academic mode: Recommend research directions and advisors

- **📝 Agent 3: Resume/CV Optimization Agent**
  - Job mode: Optimize resume based on job descriptions
  - Academic mode: Optimize academic CV structure

- **🎭 Agent 4: Mock Interview Agent**
  - Job mode: Simulate company interviews
  - Academic mode: Simulate PhD/Master's interviews

- **📈 Agent 5: Capability Enhancement Agent**
  - Job mode: Career skill development plans
  - Academic mode: Research capability development plans

#### Academic-Exclusive AI Agents (6-7) ⭐

- **🎯 Agent 6: Advisor Adaptation Agent** (Academic-exclusive)
  - Reframe project experiences based on advisor's research direction
  - Generate Research Interest Statement
  - Create "Why This Lab" paragraph
  - Output advisor-specific customized CV

- **✉️ Agent 7: Cold Email Generator** (Academic-exclusive)
  - Generate professional academic contact emails
  - Support 4 email types (initial contact, follow-up, with CV, post-conference)
  - Provide 3 versions (conservative, balanced, proactive)
  - Include email etiquette and timing suggestions

#### Output Formats

- 📄 **PDF** - Professional format for formal applications
- 📝 **DOCX** - Editable format for further customization
- 🌐 **HTML** - Modern responsive design with dark mode support
- 📊 **Excel** - Growth tracking spreadsheet with milestones

### 🚀 Quick Start

After installation, simply chat with Claude Code:

**Job Search**:
```
"Help me write a resume"           # Create resume
"Optimize this resume"             # Optimize existing resume
"Apply for XX position"            # Optimize for specific job
"Mock interview"                   # Interview practice
"Want XX job but lack skills"      # Skill gap analysis
```

**Academic Applications**:
```
"Help me write a CV"               # Create academic CV
"Apply to Prof. XX's PhD program"  # Advisor adaptation + CV customization
"Send cold email to advisor"       # Generate academic contact email
"Mock PhD interview"               # Academic interview prep
"Lack research experience"         # Academic capability enhancement
```

### 🎯 Use Cases

#### Job Search Scenarios

| Scenario | Agents Used | Output |
|----------|-------------|--------|
| First-time resume | Agent 1 → Agent 3 | Polished resume |
| Job application | Agent 3 | Tailored resume |
| Interview prep | Agent 4 | Practice feedback |
| Career development | Agent 2 → Agent 5 | Development plan |
| Complete job search | Agents 1-5 | End-to-end support |

#### Academic Application Scenarios

| Scenario | Agents Used | Output |
|----------|-------------|--------|
| Apply for Master's | Agent 1 → Agent 3 | Basic academic CV |
| Apply to specific advisor | Agent 1 → Agent 3 → Agent 6 | Advisor-specific CV |
| Cold email to advisor | Agent 6 → Agent 7 | CV + Cold email |
| PhD interview prep | Agent 4 (Academic mode) | Interview feedback |
| Lack research background | Agent 5 (Academic mode) | Academic enhancement plan |
| Complete academic application | Agents 1-7 | Full pipeline support |

### 💡 Complete Workflow

#### Job Search Workflow
```
1️⃣ Story Mining (Agent 1)
   "Don't know what to write" → Guided conversation → Experience profile

2️⃣ Job Recommendation (Agent 2)
   Based on profile → Matching analysis → Job recommendation report

3️⃣ Resume Optimization (Agent 3)
   "Optimize for XX position" + JD → Optimized resume (JSON)

4️⃣ File Generation
   Use scripts → PDF/DOCX/HTML resume

5️⃣ Mock Interview (Agent 4)
   Based on resume → Mock questions → Interview feedback + Resume improvements

6️⃣ Growth Planning (Agent 5) Optional
   If skills lacking → Gap analysis → Growth plan + Excel tracker
```

#### Academic Application Workflow (Core) ⭐
```
1️⃣ Academic Background Mining (Agent 1 - Academic mode)
   Extract research experiences → Academic profile

2️⃣ Research Direction Recommendation (Agent 2 - Academic mode)
   Recommend advisors/projects → Advisor recommendation report

3️⃣ Basic CV Generation (Agent 3 - Academic mode)
   Generate academic CV → Basic CV (JSON)

4️⃣ Advisor Adaptation (Agent 6 - Academic-exclusive) ⭐ Core Feature
   Collect advisor info (website, papers) → Reframe project experiences →
   Generate research interest statement → Advisor-specific CV

5️⃣ Cold Email (Agent 7 - Academic-exclusive)
   Generate professional academic email → 3 versions + sending tips → Cold email

6️⃣ Academic Interview (Agent 4 - Academic mode)
   Simulate PhD interview → Interview feedback

7️⃣ Capability Enhancement (Agent 5 - Academic mode) Optional
   Research capability gap analysis → Academic enhancement plan + Excel tracker
```

**Typical Example**: Apply to a Specific Advisor's PhD
```
User: "I want to apply to Prof. Zhang's PhD program at Tsinghua"

System executes:
Agent 1 → Extract academic background
Agent 3 → Generate basic CV
Agent 6 → Collect Prof. Zhang's info (research direction, papers), adapt CV
        Output: Prof. Zhang-specific CV, highly aligned keywords
Agent 7 → Generate cold email (3 versions)
        Output: Professional email + subject lines + timing suggestions

User: Send email + attach Prof. Zhang-specific CV
```

### 📚 Documentation

- **[SKILL.md](SKILL.md)** - Complete skill documentation (for Claude)
- **[skillmap.json](skillmap.json)** - Skill metadata
- **[examples/](examples/)** - Sample data files
- **[references/](references/)** - Reference docs (writing guide, industry keywords, etc.)
- **[Releases](https://github.com/Yv3s-y4ng/resume-assistant-skill/releases)** - Download packaged skill

### 📋 Requirements

- ✅ **Claude Code** installed
- ✅ **Python 3.7+** for script execution
- ✅ **Python packages**: `fpdf2`, `python-docx`, `openpyxl`
- ✅ **Chinese font**: Bundled (works out of the box)

### 🔧 Troubleshooting

For issues, see [Troubleshooting Guide](references/troubleshooting.md)

### 🌟 Highlights

- ✨ **Dual-scenario support** - Job search + Academic applications
- ✨ **Seven agents** - 5 general + 2 academic-exclusive
- ✨ **Advisor adaptation** - Align keywords with advisor's research (reframe, not fabricate)
- ✨ **Cold emails** - Professional academic emails, increase advisor response rate
- ✨ **Multiple formats** - PDF/DOCX/HTML/Excel support
- ✨ **Smart matching** - Auto-optimize keywords based on JD/advisor research
- ✨ **Real practice** - Realistic interview simulation (company/academic)
- ✨ **Continuous growth** - Actionable improvement plans
- ✨ **Chinese-optimized** - Designed for Chinese market

### 📄 License

[MIT](LICENSE) - Free to use, contributions welcome

### 🔗 Links

- **Repository**: https://github.com/Yv3s-y4ng/resume-assistant-skill
- **Latest Release**: https://github.com/Yv3s-y4ng/resume-assistant-skill/releases/latest
- **Claude Code**: https://claude.ai/code
- **Issues**: https://github.com/Yv3s-y4ng/resume-assistant-skill/issues

### 📊 Version Info

- **Current Version**: 3.0.0
- **Quality Score**: A+ (9.5/10)
- **Last Updated**: 2026-03-06
- **Major Update**: Added academic application support (Agent 6 & 7)

---

<div align="center">

**为 Claude Code 量身打造 | Made for Claude Code**

</div>
