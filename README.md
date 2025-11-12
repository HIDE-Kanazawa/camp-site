# Camp Site

キャンプ場レビューとアウトドア情報を発信するJekyllブログ

## 特徴

- **最小構成**: 余計な依存なし、GitHub Pages標準のJekyllで動作
- **SEO対応**: jekyll-seo-tag、sitemap、RSS完備
- **AdSense対応**: 設定ファイルで簡単にON/OFF可能
- **レスポンシブ**: モバイル・タブレット・デスクトップ対応
- **高速**: バニラCSS、最小限のJavaScript

## セットアップ手順

### 1. リポジトリのクローン

```bash
git clone https://github.com/yourusername/camp-site.git
cd camp-site
```

### 2. Ruby環境のセットアップ

Ruby 2.7以上が必要です。

```bash
# Rubyバージョン確認
ruby -v

# Bundlerのインストール（未インストールの場合）
gem install bundler

# 依存関係のインストール
bundle install
```

### 3. _config.ymlの設定

以下の項目を自分の環境に合わせて変更してください：

```yaml
title: "あなたのサイト名"
description: "サイトの説明文"
url: "https://yourusername.github.io"
baseurl: "/camp-site"  # リポジトリ名
author:
  name: "あなたの名前"
  email: "your.email@example.com"
```

### 4. ローカルで起動

```bash
bundle exec jekyll serve
```

ブラウザで http://localhost:4000/camp-site/ にアクセス

### 5. GitHub Pagesで公開

1. GitHubにリポジトリを作成（例: `camp-site`）
2. コードをプッシュ

```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/camp-site.git
git push -u origin main
```

3. リポジトリのSettings → Pages
4. Source: `main` ブランチ、`/ (root)` を選択
5. Save

5〜10分後に https://yourusername.github.io/camp-site/ でサイトが公開されます。

## 記事の追加方法

### 1. 記事ファイルの作成

`_posts/` ディレクトリに以下の命名規則でMarkdownファイルを作成：

```
YYYY-MM-DD-title.md
```

例: `2025-11-15-new-campsite.md`

### 2. Front Matterの記入

ファイルの冒頭に以下を記述：

```yaml
---
layout: post
title: "記事のタイトル"
date: 2025-11-15
description: "記事の説明文（SEO用）"
categories: [関東, 初心者向け]  # 任意の数
tags: [キャンプ場, 温泉, ファミリー]  # 任意の数
image: /assets/img/hero-image.webp  # ヒーロー画像
thumbnail: /assets/img/thumb-image.webp  # サムネイル
---
```

### 3. 本文の執筆

Front Matterの後に本文をMarkdownで記述：

```markdown
## 見出し2

本文テキスト

### 見出し3

- リスト1
- リスト2

![画像の説明](/assets/img/sample.webp)
```

### 4. プレビュー

```bash
bundle exec jekyll serve
```

ローカルで確認後、GitHubにプッシュすれば自動的に公開されます。

## 画像の追加方法

### 推奨仕様

- **形式**: WebP（fallbackとしてJPGも可）
- **ヒーロー画像**: 横1200px × 縦630px程度
- **サムネイル**: 横600px × 縦400px程度
- **記事内画像**: 横1200px以内

### 配置場所

`assets/img/` ディレクトリに画像を配置

### 画像の最適化

以下のツールで事前に最適化してください：

- [Squoosh](https://squoosh.app/) - オンライン画像圧縮
- [ImageOptim](https://imageoptim.com/) - Mac用
- [TinyPNG](https://tinypng.com/) - PNG/JPG圧縮

### レスポンシブ対応（オプション）

必要に応じてsrcsetを使用：

```html
<img src="/assets/img/sample.webp"
     srcset="/assets/img/sample-600.webp 600w,
             /assets/img/sample-1200.webp 1200w"
     sizes="(max-width: 600px) 100vw, 1200px"
     alt="画像の説明">
```

## タグ・カテゴリの管理

### タグの追加

記事のFront Matterに追加するだけで自動的にタグ一覧ページに表示されます。

```yaml
tags: [新しいタグ, 既存のタグ]
```

### カテゴリの追加

同様にFront Matterに追加：

```yaml
categories: [新しいカテゴリ]
```

### 個別タグ/カテゴリページの作成（オプション）

`tag/` または `category/` ディレクトリに以下のファイルを作成：

**tag/キャンプ場.md の例:**

```yaml
---
layout: list
title: "キャンプ場"
collection_type: tag
tag: キャンプ場
back_url: /tags/
back_label: タグ一覧に戻る
---
```

**category/関東.md の例:**

```yaml
---
layout: list
title: "関東"
collection_type: category
category: 関東
back_url: /categories/
back_label: カテゴリ一覧に戻る
---
```

## AdSenseの設定

### 1. AdSenseアカウントの取得

Google AdSenseに登録してサイトを審査に出す

### 2. _config.ymlの編集

```yaml
adsense:
  enabled: true  # falseをtrueに変更
  client: "ca-pub-1234567890123456"  # 自分のパブリッシャーID
  slot_inarticle: "1234567890"  # 記事内広告のスロットID
```

### 3. 広告の表示位置

- **<head>タグ内**: 自動で挿入されます
- **記事内**: `_includes/adsense.html` が記事内に自動挿入されます

## Google Analyticsの設定

### 1. Googleアナリティクスアカウントの取得

Google Analytics 4 (GA4) でプロパティを作成

### 2. _config.ymlの編集

```yaml
analytics:
  enabled: true  # falseをtrueに変更
  gtag: "G-XXXXXXXXXX"  # 自分の測定ID
```

### 3. 動作確認

サイトにアクセスして、Analytics管理画面のリアルタイムレポートで確認

## お問い合わせフォームの設定

デフォルトでは `contact.md` のformのaction属性がダミーになっています。

### Formspreeを使う場合

1. [Formspree](https://formspree.io/) でアカウント作成
2. フォームを作成してIDを取得
3. `contact.md` のaction属性を更新

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

### 他のフォームサービス

- **Netlify Forms**: Netlifyでホストする場合
- **Google Forms**: Googleフォームを埋め込み
- **Typeform**: より高度なフォーム

## カスタマイズ

### 色の変更

`assets/css/main.css` の `:root` セクションで変更可能：

```css
:root {
  --color-primary: #2c5f2d;     /* プライマリカラー */
  --color-secondary: #97bc62;   /* セカンダリカラー */
  --color-text: #333;           /* テキスト色 */
  /* ... */
}
```

### レイアウトの変更

`_layouts/` ディレクトリ内のHTMLファイルを編集

### ナビゲーションメニューの変更

`_includes/header.html` のナビゲーション部分を編集

## トラブルシューティング

### ローカルで起動しない

```bash
# Bundlerを更新
bundle update

# キャッシュをクリア
bundle exec jekyll clean
bundle exec jekyll serve
```

### GitHub Pagesでビルドエラー

- リポジトリのActions タブでエラー内容を確認
- 使用しているプラグインがGitHub Pagesのホワイトリストにあるか確認
- _config.ymlの構文エラーをチェック

### 画像が表示されない

- 画像のパスが正しいか確認（`/assets/img/`から始まる絶対パス）
- 画像ファイルが実際に存在するか確認
- baseurlの設定が正しいか確認

### スタイルが反映されない

- ブラウザのキャッシュをクリア（Ctrl+Shift+R / Cmd+Shift+R）
- CSSファイルのパスが正しいか確認

## パフォーマンス最適化

### 画像の最適化

- WebP形式を使用
- 適切なサイズにリサイズ
- 圧縮ツールで最適化

### Lighthouseスコアの確認

```bash
# Chrome DevToolsで確認
1. Chromeで自分のサイトを開く
2. F12でDevToolsを開く
3. Lighthouseタブを選択
4. Generate reportをクリック
```

目標スコア：
- Performance: 90+
- Accessibility: 90+
- Best Practices: 90+
- SEO: 90+

## ライセンス

MIT License

## サポート

質問や問題があれば、GitHubのIssuesで報告してください。

---

Happy Camping! ⛺🔥
