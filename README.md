# 雛形リポジトリをコピーして新規プロジェクトとして使う手順
（Fork せずに独立させる方法）

## 1. 元リポジトリをクローン

```bash
git clone https://github.com/元のユーザー/flutter-web-sandbox.git
cd flutter-web-sandbox
```

---

## 2. 既存の Git 履歴を削除（重要）

```bash
rm -rf .git
```

これにより、元リポジトリとの履歴・関連が完全に切れます。

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
git remote add origin https://github.com/自分のユーザー名/my-shooting-game.git
git branch -M main
git push -u origin main
```

---

## 6. GitHub Pages 用の設定を修正（重要）

### deploy.yml の base-href を新しいリポジトリ名に変更

```yaml
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
https://自分のユーザー名.github.io/my-shooting-game/
```

---

## 注意点

- `.git` を削除し忘れると、元リポジトリに push してしまう可能性があります
- リポジトリ名を変えたら `base-href` も必ず変更してください

## Optional: Rename project

This template can be used as-is, but you may want to rename it
when starting your own project.

### Folder name
```bash
mv flutter-web-sandbox my-awesome-app
cd my-awesome-app
```

### Flutter project name (Dart package name)
```bash
# pubspec.yaml
name: my_awesome_app
```

After renaming, run:
```bash
flutter pub get
```

> Note: Renaming is optional for Web-only projects.
> If you plan to target Android or iOS later, renaming is recommended.
