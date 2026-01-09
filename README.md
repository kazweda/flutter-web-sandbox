# Flutter Web Sandbox

Flutter を使った **Web アプリ開発の検証用サンドボックス**です。  
現在は Flutter 標準のカウンターアプリを Web として動作させています。

このリポジトリは、**Flutter Web + GitHub Pages デプロイ構成の雛形**としても利用できます。

---

## Demo

https://ユーザー名.github.io/flutter-web-sandbox/

---

## Features

- Flutter Web アプリ（Counter サンプル）
- GitHub Actions による自動ビルド & GitHub Pages デプロイ
- SPA 対応（404.html 設定済み）

---

## Getting Started（ローカル実行）

### Prerequisites

- Flutter (stable)
- Google Chrome

### Run locally

```bash
flutter pub get
flutter run -d chrome
```

---

## Use this repository as a template

このリポジトリは、Flutter Web プロジェクトの雛形として利用できます。

### 雛形リポジトリをコピーして新規プロジェクトとして使う手順
（Fork せずに独立させる方法）

## 1. 元リポジトリをクローン

```bash
git clone https://github.com/<original-username>/flutter-web-sandbox.git
cd flutter-web-sandbox
```

---

## 2. 既存の Git 履歴を削除（重要）

```bash
rm -rf .git
```

これにより、元リポジトリとの履歴・関連が完全に切れます。
この手順を省略すると、誤って元リポジトリに push してしまう可能性があります。

---

## 3. 新しい Git リポジトリとして初期化

```bash
git init
git add .
git commit -m "Initial commit"
```

---

## 4. GitHub で新しい空のリポジトリを作成

例：
- リポジトリ名: `my-shooting-game`
- Initialize with README: **しない**

---

## 5. 新しいリモートを登録して push

```bash
git remote add origin https://github.com/<your-username>/my-shooting-game.git
git branch -M main
git push -u origin main
```

---

## 6. GitHub Pages 用の設定を修正（重要）

### deploy.yml の base-href を新しいリポジトリ名に変更

```bash
flutter build web --release --base-href /my-shooting-game/
```

---

## 7. 動作確認（ローカル）

```bash
flutter pub get
flutter run -d chrome
```

---

## 8. main に push / merge すると自動デプロイ

```bash
git add .
git commit -m "Update project"
git push
```

GitHub Actions が実行され、
GitHub Pages にデプロイされます。

---

## 公開 URL

```
https://<your-username>.github.io/my-shooting-game/
```

---

## 注意点

- `.git` を削除し忘れると、元リポジトリに push してしまう可能性があります
- リポジトリ名を変えたら `base-href` も必ず変更してください

## （任意）プロジェクト名・フォルダ名の変更について

このリポジトリは、そのままクローンして利用できますが、  
**自分用のプロジェクトとして開発を進める場合は、名前を変更することをおすすめします。**

※ Flutter Web のみを対象とする場合、変更は必須ではありません。

---

### フォルダ名の変更（おすすめ）

ローカルでの作業を分かりやすくするため、  
リポジトリ名と同じフォルダ名に変更すると便利です。

```bash
cd ..
mv flutter-web-sandbox my-awesome-app
cd my-awesome-app
```

---

### Flutter プロジェクト名（Dart パッケージ名）の変更（任意）

`pubspec.yaml` の `name` は Dart のパッケージ名です。  
将来 Android / iOS に対応する予定がある場合は、変更しておくと安全です。

```yaml
# pubspec.yaml
name: my_awesome_app
```

変更後は、必ず依存関係を再取得してください。

```bash
flutter pub get
```

---

### 注意

- Web アプリのみの場合、この変更は **必須ではありません**
- Android / iOS に対応する予定がある場合は、早めの変更をおすすめします
- GitHub Pages 用の `base-href` は **リポジトリ名に合わせて修正**してください
