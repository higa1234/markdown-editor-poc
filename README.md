# Markdown Editor PoC

非エンジニアでも直感的に使える Markdown Editor の実現可能性を検証するための PoC リポジトリです。

このリポジトリは技術検証を目的としており、本番利用を想定したコードではありません。

## Purpose

Markdown の記法を意識せずに編集できる、WYSIWYG に近い Markdown Editor が実現可能かを検証します。

特に以下を重点的に確認します。

- Markdown を直接意識せずに編集できるか
- WYSIWYG 編集結果を Markdown として保持できるか
- Markdown → Editor → Markdown の往復変換で情報が壊れないか
- 一般的な Markdown 記法を十分に扱えるか
- 将来的に PWA / デスクトップアプリへ展開可能か

## Important

このリポジトリは PoC（Proof of Concept）です。

以下は保証しません。

- 本番品質
- 後方互換性
- API / コンポーネント設計の安定性
- セキュリティ
- パフォーマンス最適化
- アクセシビリティ対応
- テスト網羅性

検証のため、実装を大きく変更・削除する可能性があります。

本番開発を開始する場合は、この PoC をそのまま本番コードとして利用するのではなく、検証結果をもとに改めて設計・実装します。

## Scope

### 検証対象

以下の機能・技術を検証します。

- React + TypeScript によるエディタ UI
- Rich Text Editor ライブラリの利用
- Markdown の読み込み
- Markdown の書き出し
- Markdown と Editor 内部表現の相互変換
- 基本的な Markdown 要素の編集
  - 見出し
  - 太字
  - 斜体
  - 箇条書き
  - 番号付きリスト
  - リンク
  - 引用
  - コード
  - コードブロック
- Undo / Redo
- コピー＆ペースト
- Markdown ファイルの読み込み・保存

必要に応じて以下も検証します。

- テーブル
- タスクリスト
- 画像
- キーボードショートカット
- PWA
- デスクトップアプリ化

## Out of Scope

PoC では以下を原則として対象外とします。

- ユーザー認証
- クラウド同期
- 複数ユーザーによる共同編集
- バージョン管理
- 本格的なファイル管理
- プラグインシステム
- モバイルアプリ
- 本番向けインフラ
- 課金機能

## Key Technical Question

この PoC で最も重要な検証ポイントは以下です。

> Markdown を知らないユーザーが WYSIWYG として編集しながら、  
> Markdown ファイルとして自然に保存・再編集できるか。

特に、

```text
Markdown
   ↓
Editor
   ↓
編集
   ↓
Markdown
```

という往復変換を行った際に、Markdown の意味や構造が壊れないことを重視します。

## GO / NO-GO Criteria

### GO

以下の条件を満たした場合、本開発へ進む候補とします。

- 主要な Markdown 記法を WYSIWYG で編集できる
- Markdown → Editor → Markdown の往復変換が実用上問題ない
- 意図しない Markdown の破壊・消失が少ない
- Markdown を知らないユーザーでも基本操作が可能
- エディタ操作に大きな違和感がない
- 技術的に保守可能な構成にできる
- 将来的な PWA / デスクトップアプリ化に大きな制約がない

### NO-GO

以下のいずれかが重大な問題となる場合は、本開発を見送る、または技術選定を見直します。

- Markdown の往復変換で頻繁に構造が壊れる
- Markdown 固有の記法を保持することが難しい
- WYSIWYG と Markdown の両立に大きな制約がある
- エディタライブラリへの依存が強すぎる
- 実装・保守コストが想定以上に高い
- Markdown を知らないユーザーにとって操作が分かりにくい
- ファイルベースの Markdown Editor として成立しない

## Proposed Tech Stack

PoC 時点では以下を使用します。

- React
- TypeScript
- Vite
- ESLint
- Prettier

エディタ部分については、PoC の中で候補ライブラリを比較・検証します。

候補例:

- Tiptap / ProseMirror
- Lexical
- CodeMirror
- その他 Markdown 対応エディタ

## Development Policy

PoC のため、以下を優先します。

1. 技術的に可能かを確認する
2. 問題点を早期に発見する
3. 実装量を最小限にする
4. UI の完成度より技術検証を優先する
5. 本番設計を先回りしすぎない

「きれいなコードを作ること」よりも、

> このプロダクトが成立するか判断できること

を優先します。

