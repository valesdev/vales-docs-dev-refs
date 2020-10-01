# 代码管理

采用 [Git](https://git-scm.com/) 作为基本代码管理软件。

## 分支

| Git 分支 | 描述 |
| --- | --- |
| `master` | 发布分支，用于部署到生产服务器 |
| `develop` | 开发分支，用于部署到测试服务器 |
| `feature/xxx` | 功能开发分支 |
| `hotfix/xxx` | 热修复开发分支 |

## 流程

- **新功能开发流程**：从 `develop` 分支新建 `feature/xxx` 分支，并在此分支上进行开发工作，完成后合并回 `develop` 分支以进行测试；
- **热修复开发流程**：从 `master` 分支新建 `hotfix/xxx` 分支，并在此分支上进行修复工作，完成后合并回 `master` 分支和 `develop` 分支以进行发布；
- **发布流程**：将 `develop` 分支合并到 `master` 分支以进行发布；

## Commit message 格式约定

```
[类型]: <模块名称>: [变更内容] [#issue编号 [#issue编号 [#issue编号 ...]]]
```

| 类型值 | 类型描述 |
| --- | --- |
| `feat` | 新增功能 |
| `fix` | bugs 修复 |
| `docs` | 文档和注释 |
| `style` | 代码风格与拼写错误等（不涉及业务代码变更） |
| `refactor` | 重构（不涉及业务代码变更） |
| `test` | 测试代码变更（不涉及业务代码变更） |
| `chore` | 构建任务变更、包管理配置变更等（不涉及业务代码变更） |