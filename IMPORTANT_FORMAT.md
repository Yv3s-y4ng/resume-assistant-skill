# ⚠️ 重要：数据格式说明

## 问题背景

在使用resume-assistant-skill时，**最常见的错误**是生成了错误的JSON数据格式，导致简历内容为空。

## ❌ 错误格式（嵌套结构）

**不要**使用嵌套的对象结构：

```json
{
  "personal_info": {
    "name": "张三",
    "phone": "138-0000-0000",
    "email": "zhangsan@example.com"
  },
  "research_experience": [
    {
      "title": "项目标题",
      "role": "研究助理"
    }
  ]
}
```

这种格式会导致脚本无法读取数据，生成的简历将是**空白的**。

## ✅ 正确格式（扁平结构）

**必须**使用扁平的JSON结构：

```json
{
  "name": "张三",
  "phone": "138-0000-0000",
  "email": "zhangsan@example.com",
  "experience": [
    {
      "company": "项目标题",
      "position": "研究助理",
      "startDate": "2023.01",
      "endDate": "2023.12"
    }
  ]
}
```

## 📋 关键字段映射

### 求职场景

| 顶层字段 | 类型 | 说明 |
|---------|------|------|
| `name` | string | 姓名（直接在顶层，不是`personal_info.name`） |
| `phone` | string | 电话（直接在顶层） |
| `email` | string | 邮箱（直接在顶层） |
| `location` | string | 地址（直接在顶层） |
| `experience` | array | 工作经历（不是`work_experience`） |
| `projects` | array | 项目经历 |
| `education` | array | 教育背景 |
| `skills` | array | 技能列表 |

### 学术场景（CV）

学术场景使用**相同的顶层字段**，但`experience`用于研究经历：

| experience数组中的对象 | 说明 |
|---------------------|------|
| `company` | 研究项目名称（不是`title`） |
| `position` | 角色（如"研究助理"，不是`role`） |
| `organization` | 所属机构 |
| `startDate` | 开始日期（格式：2023.01） |
| `endDate` | 结束日期（格式：2023.12） |
| `tech` | 技术栈数组 |
| `details` | 详细描述数组 |

## 🔍 常见错误检查清单

生成JSON后，请检查：

- [ ] **顶层字段**：`name`、`phone`、`email`是否直接在顶层？
- [ ] **无嵌套对象**：是否有`personal_info`、`contact_info`等嵌套对象？
- [ ] **experience字段名**：是否使用`experience`而不是`research_experience`、`work_experience`？
- [ ] **company字段**：experience数组中是否使用`company`而不是`title`？
- [ ] **position字段**：experience数组中是否使用`position`而不是`role`？
- [ ] **日期格式**：是否同时包含`date`（用于显示）和`startDate`/`endDate`（用于脚本）？

## 📚 参考示例

完整的正确示例请参考：

- `examples/resume_data_example.json` - 标准格式
- `examples/fresh_graduate_example.json` - 应届生
- `examples/experienced_example.json` - 有经验者

## 🐛 如果生成的简历是空的

如果你发现生成的HTML/PDF/DOCX简历内容为空或只有标题，**99%的原因是JSON格式错误**。

**快速修复步骤**：

1. 检查JSON文件中是否有`personal_info`、`research_experience`等嵌套字段
2. 将嵌套字段提升到顶层：`personal_info.name` → `name`
3. 重命名字段：`research_experience` → `experience`、`title` → `company`、`role` → `position`
4. 重新运行脚本

## 💡 为什么使用扁平结构？

扁平结构是简历数据的行业标准：

1. **兼容性好**：与主流简历工具（LinkedIn、Indeed、Reactive Resume）格式一致
2. **易于阅读**：模板引擎可以直接访问`{{name}}`，而不是`{{personal_info.name}}`
3. **避免歧义**：统一使用`experience`字段表示工作/研究经历，无需区分`work_experience`和`research_experience`

## 🚀 最佳实践

生成简历数据时，始终：

1. 参考`examples/`目录中的示例文件
2. 使用扁平的JSON结构
3. 在生成文件前验证JSON格式
4. 如果不确定，运行`python -m json.tool data.json`检查JSON是否有效

---

**记住**：如果简历内容为空，第一时间检查JSON格式！
