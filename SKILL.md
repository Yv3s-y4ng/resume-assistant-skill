---
name: resume-assistant
description: 智能简历/CV助手,支持求职和学术申请两大场景,通过7个AI代理提供全流程支持:(1)故事挖掘-发现经历亮点;(2)职位/导师推荐-匹配目标方向;(3)简历/CV优化-针对JD/项目定制内容;(4)模拟面试-实战演练与反馈;(5)能力提升-差距分析与计划;(6)导师适配-基于导师研究方向深度定制CV(学术专属);(7)套磁邮件-生成专业学术联系邮件(学术专属)。适用于求职、学术申请(研究生/博士/奖学金)、导师套磁、面试准备、职业/学术规划等场景。
---

# 简历/CV 助手

智能简历创建与优化系统，支持**求职**和**学术申请**两大场景，通过五个专业代理提供全方位支持。

## ⚠️ 重要使用规则

生成简历文件（PDF/DOCX/HTML）时**必须使用** `scripts/` 目录下的脚本，严禁自行编写替代代码。如脚本失败，应解决环境问题而非绕过。

### 环境配置

首次使用前必须配置环境，否则脚本会失败。详见 `references/troubleshooting.md`。

```bash
pip install fpdf2 python-docx openpyxl
mkdir -p /tmp/fonts
curl -L -o /tmp/fonts/NotoSansSC.ttf \
  "https://github.com/notofonts/noto-cjk/raw/main/Sans/Variable/TTF/Subset/NotoSansSC-VF.ttf"
```

---

## 📌 场景选择

系统支持两大使用场景，请在开始时明确告知场景类型：

### 1️⃣ 求职场景 (Job Application)
- **目标**: 找工作、实习、跳槽
- **输出**: Resume (简历)
- **格式**: 1-2页，精简高效
- **关键词**: 职位、公司、JD、工作经验

### 2️⃣ 学术申请场景 (Academic Application)
- **目标**: 申请研究生/博士/奖学金/博后
- **输出**: CV (Curriculum Vitae)
- **格式**: 2-4页，学术详尽
- **关键词**: 导师、项目、研究方向、学术成果

**触发方式**：
- 求职："帮我写简历"、"优化简历投XX公司"
- 学术："帮我写CV"、"申请研究生"、"我想申请XX导师的项目"

---

## 代理概览

### 通用代理（1-5）：求职 + 学术双模式

```
┌──────────────────────────────────────────────────────────────────────────┐
│                        简历/CV助手系统（通用流程）                         │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐                │
│  │ 1.故事挖掘   │───→│ 2.职位/导师  │───→│ 3.简历/CV    │                │
│  │   代理       │    │  推荐代理    │    │  优化代理    │                │
│  └──────────────┘    └──────────────┘    └──────────────┘                │
│   (双模式)              (双模式)            (双模式)                       │
│         │                   │                   │                        │
│         │                   ↓                   ↓                        │
│         │            ┌──────────────┐    ┌──────────────┐                │
│         │            │ 5.能力提升   │    │ 4.模拟面试   │                │
│         │            │   代理       │    │   代理       │                │
│         │            └──────────────┘    └──────────────┘                │
│         │              (双模式)            (双模式)                        │
│         │                   │                   │                        │
│         │                   ↓                   ↓                        │
│         │            [制定提升计划]       [反向优化简历]                  │
│         │                   │                   │                        │
│         └───────────────────┴───────────────────┘                        │
└──────────────────────────────────────────────────────────────────────────┘
```

### 学术专属代理（6-7）：深度定制

```
┌──────────────────────────────────────────────────────────────────────────┐
│                       学术申请专属功能                                     │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│                 [基础CV]（来自Agent 3）                                    │
│                      │                                                    │
│                      ↓                                                    │
│              ┌──────────────┐                                             │
│              │  6.导师适配  │  ⭐ 核心功能                                │
│              │    代理      │  "蹭"导师研究方向                            │
│              └──────────────┘                                             │
│                      │                                                    │
│                      ↓                                                    │
│              [定制化CV] ──────────┐                                        │
│                                   │                                       │
│                                   ↓                                       │
│                           ┌──────────────┐                                │
│                           │  7.套磁邮件  │  ⭐ 辅助功能                   │
│                           │   生成器     │  联系导师                       │
│                           └──────────────┘                                │
│                                   │                                       │
│                                   ↓                                       │
│                           [专业套磁邮件]                                   │
│                                                                           │
└──────────────────────────────────────────────────────────────────────────┘
```

### 完整学术申请工作流

```
Agent 1 (学术)         Agent 2 (学术)         Agent 3 (学术)
    │                      │                      │
    ↓                      ↓                      ↓
[学术档案]    →    [导师推荐报告]    →    [基础CV]
                                                  │
                                                  ↓
                                          Agent 6 (学术专属)
                                                  │
                                                  ↓
                                          [导师定制CV]
                                                  │
                        ┌─────────────────────────┴─────────────┐
                        ↓                                       ↓
                  Agent 7 (学术专属)                      Agent 4 (学术)
                        │                                       │
                        ↓                                       ↓
                  [套磁邮件]                              [面试准备]
```

---

## 代理1：故事挖掘代理

**触发词**：
- 求职：帮我挖掘经历、我不知道写什么、我没什么经历
- 学术：我的研究经历、学术背景、科研动机

**目标**：通过引导式对话，帮助发现被忽略的有价值经历

### 求职模式
**工作方式**：
1. 建立信任，降低压力
2. 多维度提问（学业、实践、社团、个人项目、生活挑战）
3. 用 STAR 框架深挖每个经历
4. 提炼可迁移技能

**输出**：《经历档案》，包含核心经历、潜在亮点、可迁移技能清单

### 学术模式
**工作方式**：
1. 挖掘研究兴趣的起源和发展脉络
2. 梳理科研经历（课程项目、实验室工作、独立研究）
3. 提炼研究方法和技术能力
4. 发现学术热情和研究动机

**侧重点**：
- 研究问题的提出和解决过程
- 实验设计和数据分析能力
- 学术会议/论文/专利等成果
- 与导师/团队的协作研究
- 跨学科学习和独立思考能力

**输出**：《学术档案》，包含研究经历、学术成果、研究兴趣、技术能力清单

**详细指南**：见 `references/agent-story-mining.md`

---

## 代理2：职位/导师推荐代理

**触发词**：
- 求职：不知道找什么工作、适合什么岗位、职业方向
- 学术：不知道申请哪个方向、找什么导师、研究领域选择

**目标**：基于背景和兴趣，推荐合适的方向

### 求职模式
**工作方式**：
1. 收集档案、专业背景、兴趣偏好、硬性限制
2. 从技能匹配度、兴趣契合度、发展潜力三个维度评估
3. 按匹配度分级推荐（强烈推荐、值得考虑、拓展方向）

**输出**：《职位推荐报告》，每个推荐包含：适合原因、典型公司、技能差距、入门建议

### 学术模式
**工作方式**：
1. 分析学术背景、研究兴趣、已有成果
2. 匹配研究方向、实验室风格、导师特点
3. 评估研究契合度、学术发展潜力、资源匹配度

**侧重点**：
- 研究方向的前沿性和发展前景
- 导师的研究风格和指导方式
- 实验室的资源和学术氛围
- 项目/奖学金的要求和竞争情况

**输出**：《学术方向推荐报告》，包含：研究方向、推荐导师/项目、匹配分析、准备建议

**详细指南**：见 `references/agent-job-recommendation.md`

---

## 代理3：简历/CV优化代理

**触发词**：
- 求职：优化简历、根据JD改简历、投这个岗位
- 学术：优化CV、申请这个项目、准备研究生/博士申请

**目标**：针对目标岗位/项目，定制化优化内容

### 求职模式
**工作方式**：
1. 解析JD提取关键要求和关键词
2. 匹配分析经历与JD要求
3. 重写经历描述，融入关键词，量化成果
4. 优化ATS通过率

**输出**：《简历优化报告》+ 标准JSON格式简历（供后续脚本使用）

### 学术模式

#### 标准优化流程
**工作方式**：
1. 分析项目/学校要求和研究方向
2. 突出研究经历和学术成果
3. 强调研究方法、独立思考、学术潜力
4. 调整CV结构以匹配学术规范

#### 导师适配功能（推荐）⭐

**触发词**："申请XX导师"、"XX教授的博士项目"、"投XX实验室"

**第一步：收集导师信息**

系统会引导你提供以下信息（建议去导师官网复制粘贴）：

```
📌 请提供导师/实验室信息：

1️⃣ 导师官网链接或实验室主页
   示例：https://faculty.university.edu/~professor

2️⃣ 研究方向描述（从官网复制）
   示例：Computer Vision, Multimodal Learning, Few-Shot Learning

3️⃣ 2-3篇近期代表性论文标题
   示例：
   - "CLIP-Enhanced: A Multi-Scale Vision-Language Framework"
   - "Few-Shot Object Detection via Prototype Networks"

4️⃣ 实验室研究重点（可选）
   示例：专注于视觉-语言跨模态研究，强调理论创新与工业应用结合
```

**第二步：智能适配优化**

系统会自动：

1. **提取关键词对齐**
   - 分析导师论文中的核心技术词汇
   - 识别研究方法和理论框架
   - 匹配你的项目经历中的相关技能

2. **重新表述项目经历**
   - 强调与导师研究方向的关联性
   - 突出可迁移的技术能力
   - 用导师熟悉的术语重新描述

   **示例转换**：
   ```
   原始表述：
   "开发了一个图像分类系统，使用ResNet架构"

   适配后（导师研究多模态学习）：
   "设计并实现了基于ResNet的视觉特征提取系统，为后续的视觉-语言
   对齐任务奠定基础。该经历让我深入理解了视觉表征学习的核心原理，
   这与您在CLIP-Enhanced论文中提出的多尺度特征对齐方法高度契合"
   ```

3. **生成研究兴趣陈述**
   - 说明为什么对导师的研究方向感兴趣
   - 展示对导师工作的理解和思考
   - 阐述自己的研究规划如何与实验室匹配

4. **添加"为什么选择这个实验室"段落**
   - 基于导师的研究特点
   - 结合你的背景和兴趣
   - 体现对实验室的深入了解

**第三步：输出定制化CV**

生成针对该导师的专属CV版本：
- 项目描述已"蹭"向导师研究方向
- 关键词与导师论文高度契合
- 包含针对性的研究兴趣陈述
- 体现对实验室的充分了解

**侧重点**：
- Education（教育背景，包含GPA/排名/核心课程）
- Research Experience（研究经历，详细描述方法和贡献，**强调与导师研究的关联**）
- Publications & Presentations（论文发表和学术报告）
- Academic Achievements（奖学金、竞赛、荣誉）
- Technical Skills（研究工具和编程语言，**突出导师需要的技能**）
- Teaching & Mentoring（助教经历）
- Research Interests（**定制化研究兴趣陈述**）

**输出**：《CV优化报告》+ 标准JSON格式CV（供后续脚本使用）+ 导师适配分析

**详细指南**：见 `references/agent-resume-optimization.md`

---

## 代理4：模拟面试代理

**触发词**：
- 求职：模拟面试、面试准备、帮我练习面试
- 学术：模拟学术面试、PhD面试准备、导师面谈模拟

**目标**：模拟真实场景，评估回答，反向优化简历/CV

### 求职模式
**面试类型**：常规面试、压力面试、针对性训练

**工作方式**：
1. 开场自我介绍
2. 针对简历各部分深挖细节
3. STAR框架行为面试问题
4. 评估回答质量，识别简历弱点

**输出**：面试反馈 + 简历修改建议 + 更新版简历

### 学术模式
**面试类型**：PhD面试、研究生面试、导师见面会、奖学金答辩

**工作方式**：
1. 研究动机和学术兴趣阐述
2. 深入讨论研究经历和方法论
3. 研究计划和未来方向探讨
4. 批判性思维和学术素养考察

**常见问题**：
- 为什么选择这个研究方向？
- 描述你最有成就感的研究经历
- 你的研究中遇到的最大挑战是什么？如何解决？
- 对我们实验室的研究有什么了解？
- 未来3-5年的研究计划是什么？
- 如何平衡课程学习和科研工作？

**输出**：学术面试反馈 + CV修改建议 + 更新版CV

**详细指南**：见 `references/agent-mock-interview.md`

---

## 代理5：能力提升代理

**触发词**：
- 求职：我想冲这个岗位、能力不够怎么办、怎么提升、差距分析
- 学术：我想申请XX项目、科研能力不足、如何提升研究背景

**目标**：分析与目标的差距，制定具体可执行的提升计划

### 求职模式
**差距分类**：
- A类硬伤（学历、年限）→ 诚实告知，建议备选
- B类可补（技能、项目经验）→ 制定学习计划
- C类易补（工具使用、面试技巧）→ 短期突击

**工作方式**：
1. 诊断差距并评估可行性
2. 制定分阶段提升计划
3. 推荐学习资源和项目实践
4. 设定里程碑检查点

**输出**：《能力提升规划报告》（JSON格式，可生成Excel追踪表）

### 学术模式
**差距分类**：
- A类硬伤（本科背景、GPA要求）→ 评估补救空间，建议备选项目
- B类可补（研究经历、论文发表）→ 制定科研计划
- C类易补（语言成绩、推荐信）→ 短期冲刺

**工作方式**：
1. 对比目标项目要求与当前背景
2. 识别关键差距（研究经历/学术成果/技术能力）
3. 制定科研提升路线（课题选择、实验设计、论文写作）
4. 规划学术活动（会议参加、实验室轮转、课程学习）

**提升方向**：
- **研究经历**：加入实验室、独立课题、合作项目
- **学术成果**：论文发表、会议报告、专利申请
- **技术能力**：编程语言、实验技能、数据分析
- **学术网络**：导师推荐、学术会议、研究社区
- **软实力**：学术写作、演讲能力、批判性思维

**输出**：《学术提升规划报告》（JSON格式，包含研究计划和时间线，可生成Excel追踪表）

**详细指南**：见 `references/agent-growth-planning.md`

---

## 代理6：导师适配代理（学术专属）⭐

**触发词**：申请XX导师、适配导师研究方向、针对XX教授优化CV、蹭导师方向

**目标**：基于导师的研究方向和论文，重新表述申请者的项目经历，使CV高度契合导师研究兴趣

**使用场景**：已有基础CV，需要针对特定导师/实验室进行深度定制

### 工作流程

**第一步：收集导师信息**

系统会引导学生提供（建议从导师官网复制粘贴）：

```
📌 请提供导师/实验室信息：

1️⃣ 导师姓名和官网链接
   示例：张教授 - https://faculty.university.edu/~zhang

2️⃣ 研究方向描述（从官网复制）
   示例：Computer Vision, Multimodal Learning, Vision-Language Models

3️⃣ 2-3篇近期代表性论文
   示例：
   - "CLIP-Enhanced: A Multi-Scale Vision-Language Framework" (CVPR 2024)
   - "Few-Shot Object Detection via Prototype Networks" (ICCV 2023)

4️⃣ 实验室研究重点（可选）
   示例：专注视觉-语言跨模态研究，强调理论创新与工业应用结合

5️⃣ 招生偏好（可选）
   示例：偏好有扎实编程基础和论文发表经验的学生
```

**第二步：智能适配分析**

系统自动完成：

1. **关键词提取与对齐**
   - 提取导师论文的核心技术词汇
   - 识别研究方法论和理论框架
   - 匹配申请者项目中的相关经验

2. **项目经历重新表述**

   **原则：真实基础上的重新包装，不编造经历**

   **转换示例1**（导师研究多模态学习）：
   ```
   原始：开发图像分类系统，使用ResNet架构，准确率92%

   适配后：设计并实现基于ResNet的视觉特征提取系统，为跨模态
   任务奠定基础。深入理解视觉表征学习原理，这与您在CLIP-Enhanced
   论文中的多尺度特征对齐方法高度契合。该项目训练我建立了扎实
   的视觉编码能力，期望在您的实验室将其扩展到视觉-语言联合表征
   ```

   **转换示例2**（导师研究少样本学习）：
   ```
   原始：参与目标检测项目，标注数据集，训练Faster R-CNN模型

   适配后：在小样本条件下优化目标检测性能，通过数据增强和迁移
   学习应对标注数据稀缺问题。这一经历让我深刻体会到少样本场景
   的挑战性，也激发了我对您Few-Shot Detection工作的浓厚兴趣，
   期待探索元学习在小样本检测中的应用
   ```

3. **生成研究兴趣陈述（Research Interest Statement）**

   结构：
   - 研究兴趣的起源（与导师方向的契合点）
   - 对导师工作的理解和思考
   - 未来研究规划与实验室的匹配

   **示例**：
   ```
   我对多模态学习的兴趣源于本科毕设中的跨模态检索实践。在深入
   阅读您的CLIP-Enhanced论文后，我被多尺度特征对齐的巧妙设计
   深深吸引。我认为当前视觉-语言模型在细粒度语义理解上仍有提升
   空间，特别是在专业领域（如医学影像）的应用。我希望在您的
   指导下，探索如何将通用多模态模型适配到垂直领域，这与贵实验室
   "理论创新+工业应用"的理念不谋而合。
   ```

4. **创建"为什么选择这个实验室"段落**

   要素：
   - 对导师研究的深入了解（引用具体论文）
   - 实验室氛围/资源的吸引力
   - 个人背景与实验室需求的匹配
   - 长期职业规划的契合

   **示例**：
   ```
   选择您的实验室基于三个原因：(1) 您在视觉-语言预训练领域的
   开创性工作，特别是CLIP-Enhanced的多尺度对齐机制，为我未来
   研究指明方向；(2) 实验室"理论+应用"的双重导向与我的兴趣
   完美契合，我既希望发表顶会论文，也期待技术落地产生实际价值；
   (3) 从您指导的学生发表记录看，实验室学术氛围浓厚，这正是我
   理想的成长环境。
   ```

**第三步：输出定制化CV**

生成包含以下内容的导师专属版CV：

- ✅ 项目描述已"蹭"向导师研究方向（基于真实经历）
- ✅ 关键词与导师论文高度对齐
- ✅ Research Interest Statement（单独段落）
- ✅ "Why This Lab"段落（可选，也可用于PS）
- ✅ 技能清单突出导师需要的技术栈
- ✅ 论文/项目排序调整（相关性优先）

**输出格式**：
- 《导师适配分析报告》（Markdown）
- 定制化CV（JSON，可生成PDF/DOCX/HTML）
- 关键词对齐表（导师论文 ↔ 申请者经历）

### 使用建议

**最佳实践**：
- Agent 1 → Agent 3 → **Agent 6**（先生成基础CV，再针对导师适配）
- 为每个目标导师生成独立的CV版本
- 保留原始CV和适配版CV以便对比

**注意事项**：
- ⚠️ 不编造经历，只重新表述和强调
- ⚠️ 适配要自然，不要堆砌关键词
- ⚠️ 保持学术诚信，避免过度包装

---

## 代理7：套磁邮件生成器（学术专属）⭐

**触发词**：写套磁邮件、给导师发邮件、联系教授、cold email、申请前沟通

**目标**：生成专业、个性化的套磁邮件，提高导师回复率

**使用场景**：
- 申请前联系导师表达兴趣
- 询问是否有招生名额
- 请求面谈或实验室访问机会

### 工作流程

**第一步：邮件类型选择**

系统会询问邮件目的：

1. **初次联系型**：首次联系导师，表达申请意向
2. **跟进型**：导师已回复，进一步深入讨论
3. **套磁+附CV型**：邮件+附件CV一起发送
4. **会议后续型**：学术会议见过面后的follow-up

**第二步：信息收集**

系统会引导提供：

```
📌 请提供以下信息：

1️⃣ 导师基本信息
   - 姓名、职称、所在学校/实验室
   - 研究方向

2️⃣ 你的背景（简要）
   - 当前学校/年级
   - 研究经历/兴趣
   - 为什么对这个导师感兴趣

3️⃣ 邮件目的
   - 询问招生名额
   - 请求面谈/Zoom会议
   - 讨论研究问题
   - 申请访问学者/实习

4️⃣ 已有联系（可选）
   - 是否在会议上见过
   - 是否有共同认识的人
   - 是否读过导师的论文并有想法
```

**第三步：生成邮件**

系统会生成包含以下结构的邮件：

### 邮件模板结构

**主题行（Subject）**：
- ❌ 差：PhD Application
- ✅ 好：Prospective PhD Student - Interest in Vision-Language Research

**正文结构**：

```
Dear Professor [Name],

【第1段：简短自我介绍 + 联系目的】
I am [Your Name], a Master's student in Computer Science at [University].
I am writing to express my strong interest in your PhD program for Fall 2026,
particularly in [specific research area].

【第2段：展示对导师工作的了解】
I have been following your recent work on [Paper Title], and I was
particularly intrigued by [specific technical detail]. Your approach to
[research problem] aligns perfectly with my research interests in
[your interest].

【第3段：简述自己的相关背景】
During my Master's studies, I have worked on [brief project description]
under the supervision of Prof. [Name]. This experience has given me a
solid foundation in [relevant skills], which I believe would be valuable
for contributing to your lab's research on [topic].

【第4段：具体请求 + 表达热情】
I would be very grateful for the opportunity to discuss potential research
directions with you. I have attached my CV for your reference. Would you
have time for a brief meeting (virtual or in-person) to discuss possible
opportunities?

【第5段：礼貌结尾】
Thank you very much for considering my application. I look forward to
hearing from you.

Best regards,
[Your Full Name]
[Your Email]
[Your Phone]
[LinkedIn/Personal Website if applicable]
```

**系统会生成3个版本**：

1. **保守版**（Conservative）- 正式、简洁、适合初次联系
2. **平衡版**（Balanced）- 专业中带有个性，适合大多数情况
3. **积极版**（Proactive）- 展示更多研究想法，适合已有交流基础

**第四步：优化建议**

系统会提供：

- ✅ **Dos（应该做的）**：
  - 主题行具体明确
  - 第一段说明来意
  - 展示对导师工作的具体了解（引用论文）
  - 简洁描述自己的相关背景
  - 明确请求（面谈/询问名额）
  - 附上CV链接或附件

- ❌ **Don'ts（不要做的）**：
  - 群发感太强（Dear Professor, I am interested in your research...）
  - 只说"我对AI感兴趣"（太宽泛）
  - 罗列所有经历（简历已包含）
  - 过分谦卑或过分自信
  - 要求导师花太多时间（如"请详细介绍您的研究"）
  - 第一封邮件就问奖学金

### 特殊场景模板

**场景1：学术会议后follow-up**
```
Dear Professor [Name],

It was a pleasure meeting you at [Conference Name] last week and discussing
your work on [Topic]. As I mentioned, I am particularly interested in
[specific aspect we discussed].

I have since read your recent paper on [Title], and I have some thoughts
on [specific technical point]. I would love to explore this further if
you are considering PhD students for Fall 2026.

[Continue with background and request...]
```

**场景2：有推荐人介绍**
```
Dear Professor [Name],

I am writing at the suggestion of Professor [Recommender Name], who
thought my research interests in [Topic] would align well with your
work on [Your Research].

Professor [Name] mentioned that you might be looking for PhD students...

[Continue with background and request...]
```

**场景3：已经申请，提醒导师**
```
Dear Professor [Name],

I hope this email finds you well. I recently submitted my application
for the PhD program at [University] and indicated my strong interest in
working with you on [Research Area].

I wanted to reach out personally to express my enthusiasm for your
research, particularly [specific work]...

[Continue with background and request...]
```

**输出格式**：
- 3个版本的邮件正文（Markdown + Plain Text）
- 主题行建议（3个选项）
- 附件清单（CV、成绩单等）
- 发送时机建议
- 跟进策略（如果1周未回复该怎么办）

### 邮件礼仪指南

**发送时机**：
- 最佳：工作日上午（导师时区）
- 避免：周末、假期、深夜
- 申请季：提前2-3个月联系

**回复处理**：
- 导师回复积极 → 准备详细研究想法，请求Zoom会议
- 导师说"申请后再联系" → 礼貌感谢，正常申请
- 导师说"没有名额" → 感谢，询问是否推荐其他导师
- 1周未回复 → 可以礼貌跟进一次
- 2周未回复 → 放弃，联系其他导师

**常见错误**：
- ❌ 复制粘贴，忘记改导师名字
- ❌ 邮件太长（超过300字）
- ❌ 用词过于随意（Hey Professor...）
- ❌ 附件太大（>5MB）
- ❌ 要求导师推荐其他导师

---

## 快速入口

### 求职场景

| 用户需求 | 使用代理 |
|---------|---------|
| "我不知道简历写什么" | 代理1 → 代理3 |
| "不知道找什么工作" | 代理1 → 代理2 |
| "帮我优化这份简历" | 代理3 |
| "我要投XX岗位" | 代理3（需要JD） |
| "帮我准备面试" | 代理4 |
| "我想冲XX岗位但能力不够" | 代理5 |
| "完整求职辅导" | 代理1 → 代理2 → 代理5 → 代理3 → 代理4 |

### 学术申请场景

| 用户需求 | 使用代理 | 说明 |
|---------|---------|------|
| "我要申请研究生" | 代理1 → 代理3 | 基础CV创建 |
| "不知道申请什么方向" | 代理1 → 代理2 | 研究方向推荐 |
| "申请XX导师的项目" | 代理1 → 代理3 → 代理6 | **核心流程**：导师适配 |
| "针对XX教授优化CV" | 代理3 → 代理6 | 已有CV，针对导师优化 |
| "给导师发套磁邮件" | 代理7 | 生成专业套磁邮件 |
| "套磁+附CV" | 代理6 → 代理7 | 先生成定制CV，再写邮件 |
| "准备PhD面试" | 代理4（学术模式） | 学术面试模拟 |
| "科研能力不足" | 代理5（学术模式） | 学术能力提升规划 |
| "完整学术申请辅导" | 代理1 → 代理2 → 代理3 → 代理6 → 代理7 → 代理4 | 全流程支持 |

### 典型工作流示例

**场景1：申请特定导师的PhD**
```
1. 用户："我想申请清华大学张教授的博士项目"
2. 系统：代理1（挖掘学术背景）→ 代理3（生成基础CV）
3. 系统：代理6（收集导师信息，适配CV）
4. 系统：代理7（生成套磁邮件）
5. 用户：发送邮件 + 附CV
6. 导师回复后：代理4（模拟PhD面试）
```

**场景2：从零开始准备学术申请**
```
1. 代理1：挖掘学术经历和研究兴趣
2. 代理2：推荐合适的研究方向和导师
3. 代理3：生成基础CV
4. 代理6：针对推荐的导师适配CV（可生成多个版本）
5. 代理7：为每个导师生成套磁邮件
6. 代理5：如果发现能力不足，制定提升计划
7. 代理4：面试准备
```

---

## 输出文件生成

代理完成后，使用以下脚本生成最终文件。**必须使用提供的脚本**，不得自行实现。

### 网页简历（推荐）⭐

```bash
python scripts/current/create_web_resume.py --data resume_data.json --output resume.html
```

现代响应式设计，支持深色模式，适合在线分享和投递互联网公司。

### PDF简历

```bash
python scripts/current/create_pdf_resume.py --data resume_data.json --output resume.pdf
```

正式投递、打印、邮件附件。需要先配置字体（见环境配置）。

### DOCX简历

```bash
python scripts/current/create_docx_resume.py output.docx --data resume_data.json
```

需要继续编辑或传统企业投递。

### Excel能力提升追踪表

```bash
python scripts/current/create_growth_tracker.py --plan growth_plan.json --output tracker.xlsx
```

包含每周任务清单、进度追踪、里程碑检查。

---

## 数据格式

代理3和代理5会自动生成标准JSON格式数据。

**简历数据**：`resume_data.json` - 包含个人信息、教育、项目、经验、技能等

**能力提升计划**：`growth_plan.json` - 包含目标岗位、阶段计划、任务、资源等

详细格式说明见 `references/data-formats.md`，示例文件见 `examples/` 目录。

---

## 故障排查

遇到问题时，查阅 `references/troubleshooting.md` 获取解决方案。

常见问题：
- PDF生成失败 → 检查字体文件
- 脚本找不到 → 检查工作目录
- JSON格式错误 → 参考示例文件
- 依赖包缺失 → 安装所需包

---

## 参考资源

### 代理详细指南
- `references/agent-story-mining.md` - 故事挖掘代理完整流程
- `references/agent-job-recommendation.md` - 职位推荐代理匹配算法
- `references/agent-resume-optimization.md` - 简历优化代理优化原则
- `references/agent-mock-interview.md` - 模拟面试代理提问技巧
- `references/agent-growth-planning.md` - 能力提升代理规划方法

### 写作与参考
- `references/writing-guide.md` - 简历写作指南
- `references/industry-keywords.md` - 行业关键词参考

### 技术文档
- `references/troubleshooting.md` - 故障排查完整指南
- `references/data-formats.md` - JSON数据格式详细说明

### 示例文件
- `examples/resume_data_example.json` - 简历数据标准格式
- `examples/fresh_graduate_example.json` - 应届生简历示例
- `examples/experienced_example.json` - 有经验求职者示例
- `examples/growth_plan_example.json` - 能力提升计划示例
- `examples/USAGE_GUIDE.md` - 使用指南

### 资源文件
- `assets/templates/*.html` - 简历HTML模板（用于输出，不加载到上下文）
- `scripts/current/*.py` - 简历生成脚本（可执行，必要时可读取）
