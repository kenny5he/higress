# Higress への貢献

Higress のハッキングに興味がある場合は、温かく歓迎します。まず、このような意欲を非常に奨励します。そして、以下は貢献ガイドのリストです。

[[中文](./CONTRIBUTING.md)] | [[English Contributing Document](./CONTRIBUTING_EN.md)]

## トピック

- [Higress への貢献](#higress-への貢献)
  - [トピック](#トピック)
  - [セキュリティ問題の報告](#セキュリティ問題の報告)
  - [一般的な問題の報告](#一般的な問題の報告)
  - [コードとドキュメントの貢献](#コードとドキュメントの貢献)
    - [ワークスペースの準備](#ワークスペースの準備)
    - [ブランチの定義](#ブランチの定義)
    - [コミットルール](#コミットルール)
      - [コミットメッセージ](#コミットメッセージ)
      - [コミット内容](#コミット内容)
    - [PR 説明](#pr-説明)
  - [テストケースの貢献](#テストケースの貢献)
  - [何かを手伝うための参加](#何かを手伝うための参加)
  - [コードスタイル](#コードスタイル)

## セキュリティ問題の報告

セキュリティ問題は常に真剣に扱われます。通常の原則として、セキュリティ問題を広めることは推奨しません。Higress のセキュリティ問題を発見した場合は、公開で議論せず、公開の問題を開かないでください。代わりに、[higress@googlegroups.com](mailto:higress@googlegroups.com) にプライベートなメールを送信して報告することをお勧めします。

## 一般的な問題の報告

正直なところ、Higress のすべてのユーザーを非常に親切な貢献者と見なしています。Higress を体験した後、プロジェクトに対するフィードバックがあるかもしれません。その場合は、[NEW ISSUE](https://github.com/alibaba/higress/issues/new/choose) を通じて問題を開くことを自由に行ってください。

Higress プロジェクトを分散型で協力しているため、**よく書かれた**、**詳細な**、**明確な**問題報告を高く評価します。コミュニケーションをより効率的にするために、問題が検索リストに存在するかどうかを検索することを希望します。存在する場合は、新しい問題を開くのではなく、既存の問題のコメントに詳細を追加してください。

問題の詳細をできるだけ標準化するために、問題報告者のために [ISSUE TEMPLATE](./.github/ISSUE_TEMPLATE) を設定しました。テンプレートのフィールドに従って指示に従って記入してください。

問題を開く場合は多くのケースがあります：

* バグ報告
* 機能要求
* パフォーマンス問題
* 機能提案
* 機能設計
* 助けが必要
* ドキュメントが不完全
* テストの改善
* プロジェクトに関する質問
* その他

また、新しい問題を記入する際には、投稿から機密データを削除することを忘れないでください。機密データには、パスワード、秘密鍵、ネットワークの場所、プライベートなビジネスデータなどが含まれる可能性があります。

## コードとドキュメントの貢献

Higress プロジェクトをより良くするためのすべての行動が奨励されます。GitHub では、Higress のすべての改善は PR（プルリクエストの略）を通じて行うことができます。

* タイプミスを見つけた場合は、修正してみてください！
* バグを見つけた場合は、修正してみてください！
* 冗長なコードを見つけた場合は、削除してみてください！
* 欠落しているテストケースを見つけた場合は、追加してみてください！
* 機能を強化できる場合は、**ためらわないでください**！
* コードが不明瞭な場合は、コメントを追加して明確にしてください！
* コードが醜い場合は、リファクタリングしてみてください！
* ドキュメントの改善に役立つ場合は、さらに良いです！
* ドキュメントが不正確な場合は、修正してください！
* ...

実際には、それらを完全にリストすることは不可能です。1つの原則を覚えておいてください：

> あなたからの PR を楽しみにしています。

Higress を PR で改善する準備ができたら、ここで PR ルールを確認することをお勧めします。

* [ワークスペースの準備](#ワークスペースの準備)
* [ブランチの定義](#ブランチの定義)
* [コミットルール](#コミットルール)
* [PR 説明](#pr-説明)

### ワークスペースの準備

PR を提出するために、GitHub ID に登録していることを前提とします。その後、以下の手順で準備を完了できます：

1. Higress を自分のリポジトリに **FORK** します。この作業を行うには、[alibaba/higress](https://github.com/alibaba/higress) のメインページの右上にある Fork ボタンをクリックするだけです。その後、`https://github.com/<your-username>/higress` に自分のリポジトリが作成されます。ここで、`your-username` はあなたの GitHub ユーザー名です。

2. 自分のリポジトリをローカルに **CLONE** します。`git clone git@github.com:<your-username>/higress.git` を使用してリポジトリをローカルマシンにクローンします。その後、新しいブランチを作成して、行いたい変更を完了できます。

3. リモートを `git@github.com:alibaba/higress.git` に設定します。以下の2つのコマンドを使用します：

```bash
git remote add upstream git@github.com:alibaba/higress.git
git remote set-url --push upstream no-pushing
```

このリモート設定を使用すると、git リモート設定を次のように確認できます：

```shell
$ git remote -v
origin     git@github.com:<your-username>/higress.git (fetch)
origin     git@github.com:<your-username>/higress.git (push)
upstream   git@github.com:alibaba/higress.git (fetch)
upstream   no-pushing (push)
```

これを追加すると、ローカルブランチを上流ブランチと簡単に同期できます。

### ブランチの定義

現在、プルリクエストを通じたすべての貢献は Higress の [main ブランチ](https://github.com/alibaba/higress/tree/main) に対するものであると仮定します。貢献する前に、ブランチの定義を理解することは非常に役立ちます。

貢献者として、プルリクエストを通じたすべての貢献は main ブランチに対するものであることを再度覚えておいてください。Higress プロジェクトには、リリースブランチ（例：0.6.0、0.6.1）、機能ブランチ、ホットフィックスブランチなど、いくつかの他のブランチがあります。

正式にバージョンをリリースする際には、リリースブランチが作成され、バージョン番号で命名されます。

リリース後、リリースブランチのコミットを main ブランチにマージします。

特定のバージョンにバグがある場合、後のバージョンで修正するか、特定のホットフィックスバージョンで修正するかを決定します。ホットフィックスバージョンで修正することを決定した場合、対応するリリースブランチに基づいてホットフィックスブランチをチェックアウトし、コード修正と検証を行い、main ブランチにマージします。

大きな機能については、開発と検証のために機能ブランチを引き出します。

### コミットルール

実際には、Higress ではコミット時に2つのルールを真剣に考えています：

* [コミットメッセージ](#コミットメッセージ)
* [コミット内容](#コミット内容)

#### コミットメッセージ

コミットメッセージは、提出された PR の目的をレビュアーがよりよく理解するのに役立ちます。また、コードレビューの手続きを加速するのにも役立ちます。貢献者には、曖昧なメッセージではなく、**明確な**コミットメッセージを使用することを奨励します。一般的に、以下のコミットメッセージタイプを推奨します：

* docs: xxxx. 例："docs: add docs about Higress cluster installation".
* feature: xxxx. 例："feature: use higress config instead of istio config".
* bugfix: xxxx. 例："bugfix: fix panic when input nil parameter".
* refactor: xxxx. 例："refactor: simplify to make codes more readable".
* test: xxx. 例："test: add unit test case for func InsertIntoArray".
* その他の読みやすく明確な表現方法。

一方で、以下のような方法でのコミットメッセージは推奨しません：

* ~~バグ修正~~
* ~~更新~~
* ~~ドキュメント追加~~

迷った場合は、[Git コミットメッセージの書き方](http://chris.beams.io/posts/git-commit/) を参照してください。

#### コミット内容

コミット内容は、1つのコミットに含まれるすべての内容の変更を表します。1つのコミットに、他のコミットの助けを借りずにレビュアーが完全にレビューできる内容を含めるのが最善です。言い換えれば、1つのコミットの内容は CI を通過でき、コードの混乱を避けることができます。簡単に言えば、次の3つの小さなルールを覚えておく必要があります：

* コミットで非常に大きな変更を避ける；
* 各コミットが完全でレビュー可能であること。
* コミット時に git config（`user.name`、`user.email`）を確認して、それが GitHub ID に関連付けられていることを確認します。

```bash
git config --get user.name
git config --get user.email
```

* pr を提出する際には、'changes/' フォルダーの下の XXX.md ファイルに現在の変更の簡単な説明を追加してください。

さらに、コード変更部分では、すべての貢献者が Higress の [コードスタイル](#コードスタイル) を読むことをお勧めします。

コミットメッセージやコミット内容に関係なく、コードレビューに重点を置いています。

### PR 説明

PR は Higress プロジェクトファイルを変更する唯一の方法です。レビュアーが目的をよりよく理解できるようにするために、PR 説明は詳細すぎることはありません。貢献者には、[PR テンプレート](./.github/PULL_REQUEST_TEMPLATE.md) に従ってプルリクエストを完了することを奨励します。

### 開発前の準備

```shell
make prebuild && go mod tidy
```

## テストケースの貢献

テストケースは歓迎されます。現在、Higress の機能テストケースが高優先度です。

* 単体テストの場合、同じモジュールの test ディレクトリに xxxTest.go という名前のテストファイルを作成する必要があります。
* 統合テストの場合、統合テストを test ディレクトリに配置できます。
//TBD

## 何かを手伝うための参加

GitHub を Higress の協力の主要な場所として選択しました。したがって、Higress の最新の更新は常にここにあります。PR を通じた貢献は明確な助けの方法ですが、他の方法も呼びかけています。

* 可能であれば、他の人の質問に返信する；
* 他のユーザーの問題を解決するのを手伝う；
* 他の人の PR 設計をレビューするのを手伝う；
* 他の人の PR のコードをレビューするのを手伝う；
* Higress について議論して、物事を明確にする；
* GitHub 以外で Higress 技術を宣伝する；
* Higress に関するブログを書くなど。

## コードスタイル
//TBD
要するに、**どんな助けも貢献です。**