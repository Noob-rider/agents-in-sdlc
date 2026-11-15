---
title: "课程 12 - 使用 GitHub Pages 部署网站"
description: "使用 GitHub Copilot 应用配置 Pages 工作流、审查拉取请求，并验证已发布的 Space Quiz。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

使用 GitHub Pages 部署 Space Quiz，让其他人也能访问。Copilot 可以准备工作流并引导部署，但你仍需负责审查更改并确认网站已上线。

在本课程中，你将：

- 请 Copilot 配置 GitHub Pages 部署。
- 在合并前审查工作流和拉取请求。
- 跟进部署并验证已发布的网站。

## 场景

Space Quiz 已位于 GitHub 存储库中，但其他人还需要一种简单的体验方式。使用 GitHub Pages 发布这个单文件网站，即可通过公共 URL 访问，无需添加服务器或运行时依赖项。

## 请 Copilot 准备部署

> [!WARNING]
> 创建拉取请求可能会提交并推送代码。发送此提示前，请检查批准设置和目标存储库。如果选择了 **Approve all**，不要期待系统再次单独确认。

在 `space-quiz` 的 Copilot 应用会话中发送以下提示：

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## 审查工作流和拉取请求

1. 确认仅当存储库中尚无 README 时才添加它。
2. 审查拉取请求的更改，包括工作流中的构建与部署步骤、触发条件和权限。
3. 确认工作流从默认分支部署，而不是从尚未合并的拉取请求部署。
4. 请求必要的修正并审查更新后的差异。授权合并前，等待拉取请求所需的检查全部通过。

## 授权合并和部署

> [!WARNING]
> 以下提示授权智能体合并已审查的拉取请求、更改存储库的 Pages 设置并发布网站。只有在完成审查并确认存储库和拉取请求后才发送。根据批准设置，这些操作可能不会再次请求确认。

将 `<PR_NUMBER>` 替换为已审查的拉取请求编号，然后单独发送以下提示：

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![三阶段示意图：已合并的 space-quiz 拉取请求；GitHub Actions 中成功的 Deploy website 运行，包含 Build website、Upload artifact 和 Deploy to Pages 步骤；以及发布在 yourname.github.io/space-quiz/ 的 Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## 验证部署

1. 跟进 GitHub Actions 部署运行，直到成功。
2. 打开报告中的 URL，确认 Space Quiz 已加载。

如果智能体无法启用 Pages 或合并拉取请求，请按照它提供的具体说明操作。只有部署成功且网站正常加载后，才能将任务视为完成。

## 总结与后续步骤

Space Quiz 现已作为在线网站发布，你也亲自验证了部署，而不是只依赖智能体的报告。继续学习[课程 13：回顾与后续步骤][next-lesson]。

[next-lesson]: ../13-review/
