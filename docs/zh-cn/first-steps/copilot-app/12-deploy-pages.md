---
title: "课程 12 - 使用 GitHub Pages 部署网站"
description: "使用 GitHub Copilot 应用配置 Pages 工作流、审查拉取请求，并验证已发布的 Space Quiz。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

使用 GitHub Pages 部署 Space Quiz，让其他人也能访问。Copilot 可以准备工作流并指导部署，但你仍需负责审查更改并确认网站已上线。

在本课程中，你将：

- 请 Copilot 配置 GitHub Pages 部署。
- 在合并前审查工作流和拉取请求。
- 跟进部署并验证已发布的网站。

## 场景

Space Quiz 已经存储在 GitHub 仓库中，但其他人还需要一种简单的试用方式。使用 GitHub Pages 发布这个单文件网站后，用户就可以通过公共 URL 访问它，无需添加服务器或运行时依赖项。

## 请 Copilot 准备部署

> [!WARNING]
> 创建拉取请求可能会提交并推送代码。发送此提示前，请检查批准设置和目标仓库。如果选择了 **Approve all**，不要指望系统会单独请求确认。

在 `space-quiz` 的 Copilot 应用会话中发送以下提示：

```plaintext
为此仓库准备 GitHub Pages 部署。创建 GitHub Actions 工作流，在需要时构建网站，并在更改进入默认分支后将网站部署到 GitHub Pages。如果仓库中还没有 README，请添加一个，介绍此应用以及如何在本地运行它。使用这些更改创建拉取请求，并报告链接以及所需的 Pages 设置或权限。不要合并、启用自动合并、更改 Pages 设置或部署。停止并等待我审查。
```

## 审查工作流和拉取请求

1. 确认只有在仓库中尚无 README 时才添加了 README。
2. 审查拉取请求中的更改，包括工作流的构建和部署步骤、触发条件及权限。
3. 确认工作流从默认分支部署，而不是从尚未合并的拉取请求部署。
4. 请求必要的修正并审查更新后的差异。在授权合并前，等待拉取请求所需的检查全部通过。

## 批准合并和部署

> [!WARNING]
> 以下提示授权代理合并已审查的拉取请求、更改仓库的 Pages 设置并发布网站。只有在完成审查并确认仓库和拉取请求后，才发送此提示。根据批准设置，这些操作可能无需再次确认即可执行。

将 `<PR_NUMBER>` 替换为已审查的拉取请求编号，然后单独发送以下提示：

```plaintext
我已审查此仓库中的拉取请求 <PR_NUMBER>，并授权合并和部署。使用 GitHub Actions 启用 GitHub Pages，仅在所需检查通过后合并此拉取请求，并持续监控部署，直到成功。报告已上线网站的最终 URL。如果你没有启用 Pages 或合并的权限，请准确说明我需要批准或执行的操作；在网站上线前不要报告成功。
```

![三阶段示意图：已合并的 space-quiz 拉取请求；GitHub Actions 中成功运行的 Deploy website，包括 Build website、Upload artifact 和 Deploy to Pages 步骤；以及通过 yourname.github.io/space-quiz/ 访问的 Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## 验证部署

1. 持续查看 GitHub Actions 部署运行情况，直到成功。
2. 打开报告的 URL，确认 Space Quiz 可以加载。

如果代理无法启用 Pages 或合并拉取请求，请按照它提供的具体说明操作。只有部署成功且网站能够加载后，才能将任务视为完成。

## 总结和后续步骤

Space Quiz 现已作为实时网站发布；你也亲自验证了部署，而不是只依赖代理的报告。继续学习[课程 13：回顾与后续步骤][next-lesson]。

[next-lesson]: ../13-review/
