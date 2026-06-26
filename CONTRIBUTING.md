# 贡献指南

感谢你对 agent-security-skill 的关注！我们欢迎各种贡献。

## 行为准则

本项目遵循 Contributor Covenant 行为准则。参与本项目的人员应该确保他们的行为符合该准则。

## 如何贡献

### 报告问题

- 使用明确的、描述性的标题
- 提供具体的示例来演示步骤
- 描述你观察到的行为，以及预期的行为
- 注明你使用的操作系统和浏览器版本

### 提交拉取请求

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 提交新的安全研究

我们欢迎添加新的公开发布的安全研究报告！

**要求**:
- 必须是公开发布的内容
- 提供完整的来源和引用
- 保持客观性和准确性
- 遵循现有的 Markdown 格式

**新报告模板**:
```markdown
# 报告标题

**来源**: 出版方/机构  
**发布日期**: YYYY-MM-DD  
**作者**: 作者名称

## 摘要

简要说明...

## 关键发现

- 要点 1
- 要点 2

## 缓解措施

...

## 参考链接

- [原文链接]()
```

## 开发设置

1. Fork 并 clone 仓库
2. 创建虚拟环境（如果使用 Python）
3. 安装依赖
4. 创建特性分支
5. 进行更改
6. 测试你的更改
7. 提交 Pull Request

## 代码风格

- Markdown 格式: 遵循 CommonMark 规范
- 链接: 使用绝对 URL
- 代码块: 指定语言
- 列表: 使用 `-` 表示无序列表

## 提交消息规范

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Type**:
- feat: 新特性
- fix: 修复
- docs: 文档
- style: 格式
- refactor: 重构
- test: 测试
- chore: 维护

**示例**:
```
docs(security): Add supply chain attack analysis

Add comprehensive analysis of supply chain attacks
targeting AI agent systems and recommend mitigation strategies.

Fixes #123
```

## Pull Request 流程

1. 更新 README.md，说明任何新特性
2. 更新 CHANGELOG.md
3. 确保提交消息清晰
4. 获得至少一个审查者的批准

## 许可

通过提交贡献，你同意你的贡献将在项目的许可证下发布。

---

感谢贡献！🎉
