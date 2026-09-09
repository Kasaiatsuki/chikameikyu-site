# 地下迷宮の傭兵団 公開サイト

iOSアプリ「地下迷宮の傭兵団」のサポートページとプライバシーポリシーを公開するための
静的サイト。GitHub Pages で配信している。たびちず(`Kasaiatsuki/tabitizu-site`)と同じ形。

App Store Connect が **サポートURL** と **プライバシーポリシーURL** の両方を
必須項目としているため、この2つをここに置いている。

⚠️ **マーケティングURL にも同じ `index.html` を入れる。**
AdMob の app-ads.txt 検証は App Store の「デベロッパーウェブサイト」のドメインに
依存しており、**無いと検証が一生通らない**。しかもマーケティングURLは
バージョン単位のメタデータで、**販売中は編集がロックされる**ので、
**初回提出時に必ず入れる**(~/apps/KNOWLEDGE.md §6)。

| ページ | 用途 |
|---|---|
| `index.html` | サポートURL / マーケティングURL。問い合わせ先とFAQ、通報の案内 |
| `privacy.html` | プライバシーポリシーURL |

## privacy.html は生成物

**手で編集しない。** 本文の正本はアプリ本体のリポジトリの
`docs/privacy-policy.md` で、そこから生成する:

```bash
python3 ~/apps/kusoge/scripts/build-site.py ~/chikameikyu-site
```

たびちずは privacy.html を手書きしていて、README に「片方だけ直すとずれる」と
自分で注記していた。**ずれる余地を残さない**ため、こちらは生成にした
(~/apps/KNOWLEDGE.md「同じ数字を2箇所に書かない」)。

生成側は `**` や `|` が本文に残っていないかを検査して落ちる。
JSX に Markdown を書いて画面にアスタリスクが出た事故と同じ形なので、
**貼り付け先がその記法を解釈するのかを確かめる**歯止めを入れてある。

## アプリ内からもリンクする

App Store Review Guideline 5.1.1(i) は「App Store Connect のメタデータと
**アプリ内の両方**にリンクを含めること」を求めている。
アプリ側は `src/lib/legal.ts` にこのURLを持ち、設定画面から開く。
