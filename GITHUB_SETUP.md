# GitHub 项目设置指南

本文档说明如何在 GitHub 上初始化 `agent-security-skill` 项目。

## 前置步骤

1. 在 GitHub 上创建账户（如果还没有）
2. 在本地安装 Git
3. 配置 Git 用户名和邮箱：

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 在 GitHub 上创建项目

### 方法 1: 通过 GitHub Web 界面

1. 访问 https://github.com/new
2. 输入仓库名称：`agent-security-skill`
3. 输入描述：`汇集公开研究报告，对于怎么保护Agent AI`
4. 选择 **Public** 或 **Private**
5. 勾选 "Initialize this repository with:"
   - ✓ Add a README file
   - ✓ Add .gitignore
   - ✓ Choose a license (MIT)
6. 点击 **Create repository**

### 方法 2: 通过命令行

```bash
# 初始化本地仓库
git init
git add .
git commit -m "Initial commit: Add Zero Trust for AI Agents framework"

# 添加远程仓库（替换 YOUR_USERNAME）
git remote add origin https://github.com/YOUR_USERNAME/agent-security-skill.git

# 创建主分支
git branch -M main

# 推送到 GitHub
git push -u origin main
```

## 项目结构

```
agent-security-skill/
├── README.md                      # 项目说明
├── LICENSE                        # MIT 许可证
├── SKILL.md                       # Skill 定义
├── CONTRIBUTING.md                # 贡献指南
├── project.json                   # 项目配置
├── .gitignore                     # Git 忽略文件
├── zero-trust-for-ai-agents.md   # Claude Zero Trust 框架
└── research/                      # 研究报告目录（可选）
    ├── prompt-injection-attacks.md
    ├── memory-poisoning.md
    ├── supply-chain-security.md
    └── ...
```

## GitHub 最佳实践

### 1. 分支管理
```bash
# 创建特性分支
git checkout -b feature/add-supply-chain-research

# 完成后推送
git push -u origin feature/add-supply-chain-research

# 通过 Pull Request 合并到 main
```

### 2. 提交消息规范
```bash
git commit -m "docs(security): Add threat landscape analysis

- Add comprehensive threat assessment
- Include mitigation strategies
- Map to compliance requirements

Fixes #123"
```

### 3. Release 管理
```bash
# 标签版本
git tag -a v1.0.0 -m "Initial release: Zero Trust framework"
git push origin v1.0.0
```

## GitHub 配置建议

### 1. 启用 Discussions
Settings → Discussions → Enable discussions

### 2. 设置 Branch Protection
Settings → Branches → Add rule
- Require pull request reviews
- Require status checks to pass
- Require branches to be up to date

### 3. 启用 Issues
Settings → Options → Issues ✓

### 4. 配置 CI/CD（可选）
- 添加 `.github/workflows/` 目录
- 配置自动化检查和部署

## 邀请贡献者

1. 在仓库页面点击 Settings
2. 找到 "Collaborators"
3. 点击 "Add people"
4. 输入 GitHub 用户名

## 创建 Release

```bash
# 标签列表
git tag

# 创建标签
git tag -a v1.0.0 -m "Version 1.0.0: Initial Zero Trust framework"

# 推送标签
git push origin v1.0.0

# 或推送所有标签
git push origin --tags
```

## 维护项目

### 定期更新
```bash
# 同步上游更改
git fetch origin
git rebase origin/main

# 删除已合并的分支
git branch -d feature/completed-feature
```

### Issue 管理
- 使用 Labels：bug, enhancement, documentation, good-first-issue
- 创建 Issue 模板（.github/ISSUE_TEMPLATE/）
- 设置自动化响应

### Pull Request 流程
1. Fork 仓库
2. 创建特性分支
3. 提交更改
4. 创建 Pull Request
5. 经过审查和测试
6. 合并到 main

## 常见命令

```bash
# 查看状态
git status

# 查看远程
git remote -v

# 查看分支
git branch -a

# 拉取最新更改
git pull origin main

# 推送更改
git push origin main

# 删除远程分支
git push origin --delete branch-name

# 查看提交历史
git log --oneline

# 搜索历史
git log --grep="关键词" -i
```

## 故障排除

### 认证问题
- 使用 SSH：配置 SSH keys
- 使用 HTTPS：使用 Personal Access Token

### 冲突解决
```bash
# 查看冲突
git status

# 编辑冲突文件，然后：
git add .
git commit -m "Resolve conflicts"
git push
```

### 撤销更改
```bash
# 撤销最后一次提交（保留更改）
git reset --soft HEAD~1

# 撤销最后一次提交（丢弃更改）
git reset --hard HEAD~1

# 撤销已推送的提交
git revert <commit-hash>
```

---

## 接下来

1. ✅ 项目本地创建
2. 📤 推送到 GitHub
3. 📋 创建 Issues
4. 🔗 添加贡献者
5. 📢 宣传项目

**需要帮助？** 参考 [GitHub 官方文档](https://docs.github.com/)
