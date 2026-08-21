# application-terms

iOSアプリごとのプライバシーポリシーをMarkdownで管理し、GitHub Pagesで公開するためのリポジトリです。

## 新しいアプリを追加する

1. `_templates/privacy-policy.md` を `_apps/<slug>.md` としてコピーします。`<slug>`には英小文字、数字、ハイフンのみを使用してください。
2. Front Matterの `app_name`、`last_updated`、`permalink` を変更します。
3. コメントに従って本文をアプリの実態に合わせます。該当しない選択肢や説明用コメントは削除し、曖昧な記述やプレースホルダーを残さないでください。
4. ローカルで表示とリンクを確認してから公開します。

各ポリシーには次のFront Matterが必要です。

```yaml
---
layout: default
title: プライバシーポリシー
app_name: アプリ名
last_updated: YYYY-MM-DD
permalink: /apps/<slug>/
---
```

トップページの一覧は `_apps` 内のファイルから自動生成されます。ポリシーの公開URLは次の形式になります。

```text
https://<GitHubユーザー名>.github.io/<リポジトリ名>/apps/<slug>/
```

## ローカルで確認する

RubyとBundlerを用意し、依存関係をインストールします。

```shell
bundle install
bundle exec jekyll serve --baseurl "/application-terms"
```

ブラウザで `http://localhost:4000/application-terms/` を開きます。静的ファイルの生成だけを確認する場合は、次を実行します。

```shell
bundle exec jekyll build --baseurl "/application-terms"
```

## GitHub Pagesで公開する

1. GitHubへリポジトリを作成して `main` ブランチをpushします。
2. リポジトリの **Settings > Pages** を開きます。
3. **Build and deployment** のSourceで **Deploy from a branch** を選択します。
4. Branchに `main`、フォルダーに `/ (root)` を指定して保存します。
5. デプロイ完了後、HTTPSの公開URLへログインなしでアクセスできることを確認します。

## App Store Connectへ登録する

1. App Store Connectで対象アプリを開き、サイドバーの **App Privacy** を選択します。
2. **Privacy Policy** の編集画面に、対象アプリの公開URLを入力します。
3. App Privacyのデータ収集に関する質問へ回答し、公開します。
4. iOSアプリ内の設定画面など、利用者が容易にアクセスできる場所にも同じURLへのリンクを設置します。

User Privacy Choices URLは任意です。このリポジトリでは専用ページを用意しません。

## 公開前チェックリスト

- [ ] 公開ページにプレースホルダーや説明用コメントが残っていない
- [ ] アプリ本体と、広告・解析・クラッシュ収集などの第三者SDKが取得するデータをすべて確認した
- [ ] 取得するデータ、取得方法、利用目的が実態どおりに記載されている
- [ ] 第三者への提供先、目的、対象データが実態どおりに記載されている
- [ ] データの保存期間または決定基準と、削除方法が記載されている
- [ ] 同意の撤回方法とデータ削除の依頼方法が記載されている
- [ ] 問い合わせ先が有効である
- [ ] ポリシーの内容とApp Store ConnectのApp Privacy回答が一致している
- [ ] HTTPSの公開URLへログインなしでアクセスできる
- [ ] iOSアプリ内から公開URLへ容易にアクセスできる

## 注意事項

このリポジトリはAppleの審査要件に対応するための技術的な下地です。各アプリおよび配信地域に適用される法令への適合性を保証するものではありません。必要に応じて専門家へ確認してください。

対象はiOSアプリです。tvOS向けのApple TV Privacy Policy、多言語対応、利用規約、Cookieポリシー、User Privacy Choices専用ページは含みません。

## 参考資料

- [Manage app privacy - App Store Connect Help](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-app-privacy)
- [App Review Guidelines 5.1.1 - Data Collection and Storage](https://developer.apple.com/app-store/review/guidelines/#data-collection-and-storage)
- [App privacy - App Store Connect Reference](https://developer.apple.com/help/app-store-connect/reference/app-information/app-privacy)
