# GitFlow 规范

## 📌 分支模型

```
master (受保护)
  ↑
  │   通过 PR 合并
  │
dev (开发分支)
  ↑
  │
feature/* (功能分支)
```

## 🌿 分支说明

| 分支 | 用途 | 命名规范 |
|------|------|---------|
| `master` | 稳定可发布版本 | 固定名称 |
| `dev` | 开发主分支 | 固定名称 |
| `feature/*` | 新功能开发 | feature/功能名-日期 |
| `fix/*` | Bug 修复 | fix/问题描述-日期 |
| `refactor/*` | 代码重构 | refactor/模块名-日期 |

## 🔀 开发流程

### 1. 开始新功能
```bash
git checkout dev
git checkout -b feature/车牌识别-20260330
```

### 2. 开发完成后提交
```bash
git add .
git commit -m "feat: 添加车牌识别模块"
git push -u origin feature/车牌识别-20260330
```

### 3. 合并到 dev（通过 PR）
- 在 GitHub/Gitee 网页上创建 Pull Request
- Review 通过后合并到 `dev`
- 合并后删除功能分支

## 📝 Commit 规范

### 格式
```
<type>: <subject>

<body> (可选)
```

### Type 类型

| 标识 | 含义 |
|------|------|
| `feat` | 新功能 |
| `fix` | Bug 修复 |
| `refactor` | 重构（不改变功能） |
| `docs` | 文档更新 |
| `style` | 代码格式（不影响运行） |
| `test` | 测试相关 |
| `chore` | 构建/工具变更 |

### 示例
```
feat: 添加 ROS 地图加载模块

- 支持 ROS1 模型加载
- 支持 ROS2 模型加载
- 添加材质纹理自动匹配

Closes #12
```

## 🛡️ 规范

1. **禁止直接推送 master** — 所有变更通过 PR
2. **dev 分支保持最新** — 每天开始前 pull dev 最新代码
3. **功能分支及时合并** — 功能完成后尽快合并，不要拖太久
4. **Commit 信息清晰** — 让人能看懂改了啥

## 📦 当前仓库

| 平台 | 地址 |
|------|------|
| **GitHub** | github.com/2032973897-source/CITY-CHECKER_NIKO |
| **Gitee** | gitee.com/napleo/city-checker_-niko |

### 远程仓库使用
```bash
# 推送到 GitHub
git push github feature/xxx

# 推送到 Gitee
git push gitee feature/xxx

# 同时推送到两个平台
git push github dev master
git push gitee dev master
```
