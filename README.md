# shun-NMR93.github.io

[blank folio](https://github.com/NxTEND-THE-HACK/2026-Team-28) で生成したポートフォリオサイトです。

公開URL: https://shun-NMR93.github.io

## ファイル構成

| ファイル | 役割 | もう一度生成したとき |
| --- | --- | --- |
| `css/variables.css` | 色・フォント・余白の設定。**まずはここを編集** | **編集した内容が残る** |
| `css/custom.css` | 自由にスタイルを書き足す場所 | **編集した内容が残る** |
| `profile.json` | 名前・自己紹介・説明文の保存先 | **編集した内容が残る** |
| `index.html` | サイト本体 | 作り直される |
| `css/base.css` | レイアウトの実装。基本的に触らない | 作り直される |
| `README.md` | このファイル | 作り直される |

**編集していいのは上の3つ**です。下の3つに手を加えても、次にポートフォリオを生成したときに元に戻ります。

## 名前と自己紹介を変える

`profile.json` に保存されています。

```json
{
  "displayName": "表示名",
  "tagline": "自己紹介",
  "skills": ["React", "TypeScript", "Next.js"],
  "socialLinks": [
    { "platform": "twitter", "url": "https://x.com/example" }
  ],
  "layoutPattern": "standard",
  "repositories": [
    {
      "name": "example-app",
      "generatedText": "AIが書いた説明文",
      "appealText": "",
      "sourceHash": "..."
    }
  ]
}
```

`socialLinks` の `platform` は `twitter` / `github` / `zenn` / `qiita` / `other` のいずれかです。それ以外の値やhttp(s)以外のURLは表示されません。

## リポジトリの説明文を自分で書く

カードに出る説明文は `repositories` に保存されています。

| フィールド | 意味 |
| --- | --- |
| `generatedText` | AIが書いた文章。**READMEを更新すると書き直される** |
| `appealText` | あなたが書く欄。**空でなければこちらが表示される** |
| `sourceHash` | 作り直しの要否を判断するための内部用の値。触らなくて構いません |

`appealText` が空のあいだは、AIが書いた `generatedText` が表示されます。**READMEを書き足してからもう一度生成すると、新しいREADMEを読んで説明文が作り直されます。** リポジトリを育てるほど紹介文もよくなります。

READMEを変えていなければ文章は変わりません。気に入った文章があれば、**`generatedText` から `appealText` にコピーすると完全に固定できます**（以後そのリポジトリではAIが呼ばれません）。

```json
{
  "name": "example-app",
  "generatedText": "AIが書いた説明文",
  "appealText": "自分で書いた説明文（こちらが表示される）"
}
```

またAIに任せたくなったら、`appealText` を `""` に戻してもう一度生成してください。

READMEを変えていないのに説明文を作り直したいときは、`generatedText` を `""` にしてから生成してください。

`layoutPattern` に下記以外の値を入れても `standard` として扱われます。指定できる値は次のとおりです。

| 値 | 内容 |
| --- | --- |
| `standard` | 既定。SNSアイコンはヘッダー右上に固定、スキルはリポジトリ一覧の上 |
| `skills-bottom` | スキルバッジをリポジトリ一覧の下に移動する |
| `socials-inline` | SNSアイコンの右上固定をやめ、プロフィールのすぐ下に通常の行として並べる |

blank folio の入力欄から変更するのが簡単ですが、このファイルを直接編集しても構いません。**入力欄を空のまま生成した場合、ここに保存されている内容がそのまま使われます**（消えません）。

逆に言うと、**一度書いた内容を入力欄から空に戻すことはできません**。消したい場合はこのファイルの値を空文字にしてください。

## まずは variables.css から

色やフォントを変えるだけなら、`css/variables.css` の値を書き換えるだけで済みます。CSSの書き方を知らなくても、値の部分だけ変えれば反映されます。

### 色を変える

```css
--color-background: #ffffff;  /* ページ背景色 */
--color-surface: #f5f5f5;     /* カード背景色 */
--color-text: #1a1a1a;        /* 通常テキスト色 */
--color-text-muted: #6b6b6b;  /* 説明文などの薄いテキスト色 */
--color-accent: #2563eb;      /* リンクや強調箇所の色 */
--color-border: #e5e5e5;      /* 枠線の色 */
```

例: アクセント色を赤にする

```css
--color-accent: #ef4444;
```

### フォントを変える

```css
--font-family-base: "Helvetica Neue", Arial, "Hiragino Sans", sans-serif;
```

左から順に試され、見つからなければ次のフォントが使われます。フォント名にスペースが含まれる場合はクォートで囲んでください。

例: 日本語フォントを優先する

```css
--font-family-base: "Hiragino Kaku Gothic ProN", "Meiryo", sans-serif;
```

### 余白と角丸を変える

```css
--radius-base: 8px;    /* 角丸の大きさ。0px にすると角ばる */
--spacing-unit: 8px;   /* 余白の基本単位。大きくすると全体がゆったりする */
```

### 名前と自己紹介の揃え方を変える

```css
--header-name-align: left;     /* 名前 */
--header-tagline-align: left;  /* 自己紹介 */
```

`left`（左揃え）か `center`（中央揃え）を指定します。初期状態は左揃えで、名前・自己紹介・Projects の見出しがすべて同じ位置から始まります。

例: 短い一言なので中央に置きたい

```css
--header-name-align: center;
--header-tagline-align: center;
```

例: 名前だけ中央に置く

```css
--header-name-align: center;
--header-tagline-align: left;
```

**自己紹介が3行以上あるなら `left` のままをおすすめします。** 中央揃えの長い文章は行の始まる位置が毎行ずれるため、読みにくくなります。

## さらに調整したいときは custom.css

`css/custom.css` は空のまま用意してあります。ここに書いたスタイルが最後に適用されます。

```css
/* カードに影を付ける */
.portfolio-project-card {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* ヘッダーに背景を付ける（本文と同じ幅の範囲に適用されます） */
.portfolio-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

/* カードの最小幅を広げる */
.portfolio-projects__list {
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
}

/* アピール文を目立たせる */
.portfolio-project-card__appeal {
  color: #ef4444;
  font-weight: 700;
}
```

クラス名は `index.html` を開けば確認できます。`ブロック名__要素名` の形で統一されています。

## 注意

- **変更の反映には時間がかかります。** push してから GitHub Pages に反映されるまで、通常1分ほど待つ必要があります
- **見た目が変わらないときはブラウザの再読み込みを試してください。** ブラウザがCSSを一時的に保存しているため、10分ほど古い表示が残ることがあります。`Command + Shift + R`（Windowsは `Ctrl + Shift + R`）で強制的に読み込み直せます
- **設定を初期状態に戻したいときは、`css/variables.css` を削除**してからもう一度生成してください。中身を空にするだけだと「編集したファイル」として扱われ、作り直されません
- `css/base.css` はレイアウトの土台です。崩れる原因になりやすいので、まずは `variables.css` と `custom.css` で試すことをおすすめします
