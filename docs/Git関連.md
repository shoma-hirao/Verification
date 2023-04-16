- [はじめに](#はじめに)
- [ブランチ構成](#ブランチ構成)
- [ブランチの保護設定](#ブランチの保護設定)
- [コミットメッセージのテンプレート](#コミットメッセージのテンプレート)
- [プルリクエストのテンプレート](#プルリクエストのテンプレート)
- [フォルダ構成](#フォルダ構成)

## はじめに

GitHub関連で行った設定について整理した資料である。ただし、一部諸々の理由により**[保留]**にしている項目がある。

## ブランチ構成

今回は検証用のためdev環境しか用意しないが、本番運用を想定して`main`,`stg`,`dev`,`topic`ブランチは用意する。

| ブランチ名 | 用途                                                                |
| ---------- | ------------------------------------------------------------------- |
| main       | 本番環境で動くソースを管理するためのブランチ<br>stg環境と同じソース |
| stg        | STG環境での動作確認用<br>devブランチからのマージのみ可能            |
| dev        | DEV環境での動作確認用                                               |
| topic      | 実装単位でdevブランチから作成する                                   |

**[保留]**topicブランチの命名規則はタスクを何で管理するかに依存するため。

## ブランチの保護設定

[ブランチ保護ルールを管理する - GitHub Docs](https://docs.github.com/ja/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)を参考に設定。

**[保留]**個人開発で管理者権限のユーザーしかいないため、ブランチ保護のルールが適用されているかが確認できない。[こちらの記事](https://maasaablog.com/development/git/github/2881/)をみると、管理者権限のユーザーブランチ保護のルールを適用するには`include administrators`を設定する必要があるようだが、現在の設定画面には存在しないため。

## コミットメッセージのテンプレート

[【今日からできる】コミットメッセージに 「プレフィックス」 をつけるだけで、開発効率が上がった話 - Qiita](https://qiita.com/numanomanu/items/45dd285b286a1f7280ed)

を参考にする。

| prefix    | 説明                                                                 | description                                                                                            |
| --------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| feat:     | 新機能                                                               | A new feature                                                                                          |
| fix:      | バグフィックス                                                       | A bug fix                                                                                              |
| docs:     | ドキュメントの変更のみ                                               | Documentation only changes                                                                             |
| style:    | コードの意味に影響を与えない変更（空白、書式、セミコロンの欠落など） | Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc) |
| refactor: | バグを修正するわけでもなく、機能を追加するわけでもないコード変更     | A code change that neither fixes a bug nor adds a feature                                              |
| perf:     | パフォーマンスを向上させるコード変更                                 | A code change that improves performance                                                                |
| test:     | 欠落しているテストの追加や既存のテストの修正                         | Adding missing or correcting existing tests                                                            |
| chore:    | ビルドプロセスやドキュメント生成などの補助ツールやライブラリの変更   | Changes to the build process or auxiliary tools and libraries such as documentation generation         |

## プルリクエストのテンプレート


## フォルダ構成

- 個人での検証用のため、backとfrontでリポジトリを分けない
- VSCodeの設定に関してルートフォルダ直下にはファイル保存時にフォーマットチェックを行う機能の有効化など共通の設定だけ行い、backとfrontで異なる設定はそれぞれのフォルダ直下に配置し、VSCodeを2つ起動して開発を進める
