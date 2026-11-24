---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot アプリを使って Pages ワークフローを構成し、その pull request をレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages で Space Quiz をデプロイして、公開しましょう。Copilot はワークフローを準備し、デプロイを案内できますが、変更をレビューしてサイトが公開されたことを確認するのはユーザーの役割です。

このレッスンでは、次のことを行います。

- Copilot に GitHub Pages のデプロイ構成を依頼します。
- マージする前にワークフローと pull request をレビューします。
- デプロイを確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、手軽に試せる方法が必要です。単一ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに公開 URL からアクセスできるようになります。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> pull request を作成すると、コードが commit されて push されることがあります。このプロンプトを送る前に、承認設定と送信先のリポジトリを確認してください。**Approve all** が選択されている場合、個別の確認プロンプトは表示されないものとして扱ってください。

`space-quiz` の Copilot アプリ セッションで、次のプロンプトを送信します。

```plaintext
このリポジトリの GitHub Pages デプロイを準備してください。必要に応じて Web サイトをビルドし、変更が既定のブランチに反映された後に GitHub Pages へデプロイする GitHub Actions ワークフローを作成してください。README がまだない場合は、アプリとローカルでの実行方法を説明する README を追加してください。これらの変更を含む pull request を作成し、そのリンクと必要な Pages の設定または権限を報告してください。マージ、自動マージの有効化、Pages 設定の変更、デプロイは行わないでください。作業を停止してレビューを待ってください。
```

## ワークフローと pull request をレビューする

1. README は、リポジトリにまだない場合にのみ追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順、トリガー、権限を含め、pull request の変更をレビューします。
3. マージされていない pull request ではなく、既定のブランチからデプロイされることを確認します。
4. 必要な修正を依頼し、更新された diff をレビューします。マージを承認する前に、必須の pull request チェックが成功するまで待ちます。

## マージとデプロイを承認する

> [!WARNING]
> 次のプロンプトは、レビュー済みの pull request のマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを完了し、リポジトリと pull request を確認した後にのみ送信してください。承認設定によっては、これらの操作が追加の確認なしに実行されることがあります。

`<PR_NUMBER>` をレビューした pull request の番号に置き換え、別のプロンプトとして送信します。

```plaintext
このリポジトリの pull request <PR_NUMBER> をレビューし、マージとデプロイを承認しました。GitHub Actions を使って GitHub Pages を有効にし、必須チェックが成功した後に限り、その pull request のみをマージしてください。デプロイが成功するまで監視し、公開された Web サイトの最終 URL を報告してください。Pages を有効にしたりマージしたりする権限がない場合は、何を承認または実行する必要があるかを正確に伝えてください。サイトが公開されるまでは成功と報告しないでください。
```

![3 段階の図: マージ済みの space-quiz pull request、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions の Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages の有効化や pull request のマージを実行できない場合は、提示された具体的な手順に従います。デプロイが成功し、公開サイトが読み込まれるまで完了と見なさないでください。

## まとめと次のステップ

Space Quiz を公開サイトとして利用できるようにし、エージェントの報告だけに頼らずデプロイを確認しました。[レッスン 13: レビューと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
