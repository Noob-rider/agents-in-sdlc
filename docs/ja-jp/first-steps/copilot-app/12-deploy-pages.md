---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot アプリで Pages ワークフローを設定し、プルリクエストをレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages に Space Quiz をデプロイして、公開 URL から利用できるようにします。Copilot はワークフローの準備やデプロイ手順の案内を行えますが、変更をレビューし、サイトが公開されたことを確認するのはユーザーの責任です。

このレッスンでは、次のことを行います。

- Copilot に GitHub Pages へのデプロイ設定を依頼します。
- マージする前にワークフローとプルリクエストをレビューします。
- デプロイの進行状況を確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、誰でも簡単に試せる方法が必要です。単一ファイルのサイトを GitHub Pages で公開すれば、サーバーやランタイム依存関係を追加せずに公開 URL から利用できます。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> プルリクエストを作成すると、コードがコミットおよびプッシュされることがあります。このプロンプトを送る前に、承認設定と送信先のリポジトリを確認してください。**Approve all** が選択されている場合、別途確認が求められるとは限りません。

`space-quiz` の Copilot アプリ セッションで、次のプロンプトを送信します。

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## ワークフローとプルリクエストをレビューする

1. リポジトリに README がまだない場合に限って追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順、トリガー、権限を含め、プルリクエストの変更をレビューします。
3. マージされていないプルリクエストではなく、既定のブランチからデプロイされることを確認します。
4. 必要な修正を依頼し、更新後の差分をレビューします。マージを許可する前に、必須のプルリクエスト チェックがすべて成功するまで待ちます。

## マージとデプロイを許可する

> [!WARNING]
> 次のプロンプトは、レビュー済みのプルリクエストのマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを完了し、リポジトリとプルリクエストを確認してから送信してください。承認設定によっては、別の確認が表示されずにこれらの操作が実行されることがあります。

`<PR_NUMBER>` をレビューしたプルリクエストの番号に置き換え、別のプロンプトとして送信します。

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![3 段階の図: マージ済みの space-quiz プルリクエスト、Build website、Upload artifact、Deploy to Pages の各ステップが成功した GitHub Actions の Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 表示された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages の有効化やプルリクエストのマージを実行できない場合は、案内された具体的な手順に従ってください。デプロイが成功し、公開サイトが読み込まれるまで、作業を完了と見なさないでください。

## まとめと次のステップ

Space Quiz を公開サイトとして利用できるようにし、エージェントの報告に頼らずデプロイを確認しました。続けて [レッスン 13: 振り返りと次のステップ][next-lesson] に進みます。

[next-lesson]: ../13-review/
