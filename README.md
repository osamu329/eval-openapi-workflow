## OpenAPI スキーマをレビューするためのWorkflowの実験

### 前提条件

- Redocly CLI でopenapi スキーマからドキュメント生成しながらレビューするプロセスを行っている
- PR毎にドキュメントを生成して、GitHub Pages でホストする
- PATを利用できる
- package.json に @redocly/cli がインストールされている


### 試作したワークフロー

#### PRのAPIドキュメントのプレビュー作成

* OpenAPI のスキーマを編集してPR を作成すると、GitHub Actions でredocly を呼び出してドキュメントを生成して、GitHub Pages (gh-pages) にプッシュする。
  PRに対応するAPIドキュメントは `/pr-<PR number>/index.html` に生成されるため、平行して実施している別のPRの生成ドキュメントを上書きしない。

* 更新したドキュメントを、PRコメントとしてポストする。
  レビュアーは、PRコメントのリンクから生成されたドキュメントを確認できる。

* PR がクローズされると、gh-pages ブランチの対応するAPIドキュメントを削除するアクションが実行される。
