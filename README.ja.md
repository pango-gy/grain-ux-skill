# grain — AIエージェント向けUXレビュースキル

> 人が実際に考え、読み、判断し、信頼し、回復する流れに沿って設計する。

**Languages:** [English](README.md) | [한국어](README.ko.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md)

[Pango Gy](https://pango-gy.com) が管理しています。

`grain` は、ユーザーに見えるプロダクト上の判断をレビューし、整えるためのポータブルなAIエージェントスキルです。ビジュアルテーマ、コンポーネントライブラリ、デザインシステムではありません。フロー、フォーム、エラー、AIアクション、権限プロンプト、ボタンラベルが実ユーザーの行動に反しているときに指摘するUX判断レイヤーです。

フロントエンドビルダー、デザインシステムスキル、UIキット、プロダクトコードレビューと併用してください。それらがエージェントにインターフェースを作らせる道具だとすれば、`grain` はそのインターフェースがユーザーの努力、注意、アクセシビリティ、信頼、回復を尊重しているかを確認します。

## インストール

```bash
npx skills add pango-gy/grain-ux-skill
```

インストーラーは対応するAIツールを検出し、それぞれに `grain` を作成します。更新するときも同じコマンドを再実行してください。

削除:

```bash
npx skills remove grain
```

## いつ起動するか

`grain` はユーザーに影響する判断で自動的に起動します。

- UIコンポーネント、画面、フォーム、フローの作成、リファクタリング、レビュー
- 空、読み込み中、失敗、部分成功、オフライン、権限拒否状態の設計や批評
- コピー、ラベル、マイクロコピー、エラーメッセージ、オンボーディング、通知の作成
- アクセシビリティ、キーボード操作、フォーカス順、タッチターゲット、モーション、レスポンシブ挙動の確認
- フォーム、インポート、フィルター、設定、権限、共有、課金、AI出力、自動化の設計
- スクリーンショット、プロトタイプ、ダッシュボード、社内ツール、管理画面、SaaSワークフローのレビュー

バックエンド専用ロジック、インフラ、ユーザーに見える挙動がない作業では静かにしているべきです。

## 対象領域

7つの領域を、1つの視点で扱います。

- **ユーザーフローと情報設計** — ページより経路、テーブルよりタスク。
- **認知負荷とシンプルさ** — クリック数だけでなく、判断数を減らす。
- **フォームと入力** — すべての入力欄にはコストがあり、バリデーションは叱るのではなく助ける。
- **アクセシビリティと包摂的インタラクション** — キーボード、タッチ、フォーカス、モーション、コントラスト、ビューポートは基本UX。
- **信頼、同意、主体性** — 予期しない送信、共有、課金、削除、AIコミット、自動化を防ぐ。
- **エラー、エッジケース、回復** — 空/読み込み/失敗/オフライン状態を製品の一部として扱う。
- **マイクロコピーとトーン** — ボタンは結果を語り、エラーはユーザーを責めず、すべての文は声に出して読める。

各領域の詳細な基準は [`skill/references/`](skill/references) にあります。`SKILL.md` は、どの場面でどのreferenceを読むべきかを示し、メインスキルを集中した状態に保ちます。

## 中心となる考え方

`grain` はまず次の原則を適用します。

- 次の行動を明確にする。
- ユーザーの努力を守る。
- ユーザーを驚かせない。
- 確認させるだけでなく、取り消せるようにする。
- アクセシビリティをモードではなく基本UXとして扱う。
- 失敗状態を製品の一部として設計する。

すべての原則、領域ルーティング、アンチパターンは [`skill/SKILL.md`](skill/SKILL.md) にあります。

## 位置づけ

`grain` は companion skill として最も力を発揮します。

- **フロントエンドビルダー**と組み合わせると、コードが入る前にUXの後退を見つけます。
- **デザインシステム**と組み合わせると、コンポーネントが見た目だけでなく適切なタスクに使われているかを確認します。
- **AI/自動化ツールスキル**と組み合わせると、永続的または外部に影響するアクションの前に preview、consent、status、history、explicit approval を求めます。
- **プロダクトレビューのワークフロー**と組み合わせると、曖昧なフィードバックを具体的な原則とアンチパターンに変換します。

ビジュアルアイデンティティを生成したり、ブランドカラーを選んだり、プロダクトリサーチを置き換えたりはしません。エージェントがコーディングやレビュー中にすでに行っている判断に、再利用可能なUX基準を与えます。

## レビュープロンプト例

```text
Use grain to review this checkout flow for trust, consent, and recovery.
```

```text
Use grain while refactoring this settings form. Preserve input and improve validation UX.
```

```text
Use grain to check whether this AI-generated email flow needs preview, edit, and approval states.
```

```text
Use grain to review this dashboard for cognitive load, accessibility, and empty states.
```

## 作者

Pango Gy CTO 유승재 ([pinkyooysj@pango-gy.com](mailto:pinkyooysj@pango-gy.com))

会社: [Pango Gy](https://pango-gy.com)

## ライセンス

[MIT](LICENSE)。使用、フォーク、自分の言葉への書き換えができます。より多くのプロダクトがUXを第一級の関心事として扱うことが目的です。

## 系譜

Donald Norman、Jakob Nielsen、Steve Krug、Bruce Tognazzini、Alan Cooper、Dan Saffer、Edward Tufte の考えの上に立っています。どの考えがどこから来ているかは [`skill/SKILL.md`](skill/SKILL.md) の `Lineage` セクションを参照してください。
