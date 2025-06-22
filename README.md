## README

プロジェクト開始用のテンプレート

## 開始までのフロー

まず[claude-code-best-practices](https://www.anthropic.com/engineering/claude-code-best-practices)を読むこと。  
理解すれば Claude Code での開発効率が段違いに上がる。

特に CLAUDE.md の働きをよく理解すること。

1. このリポジトリを clone する。
1. devcontainer で立てる。（node が動く Ubuntu 系）
1. claude を実行・認証する。
1. gh auth login でログインする。
1. ルートにプロジェクトディレクトリを作る。  
   Create_AppDir_at_SAME_LEVEL_as_this は削除する。
1. CLAUDE.md の説明を参考に CLAUDE.md を再生成する。
1. CLAUDE.md を要件に合わせて修正する。

開発開始！

## 開発フロー

### 概要

1. GitHub で issue 作成
1. プラン作成
1. 実装
1. レビュー
1. PR 作成
1. マージ

ベストプラクティスに則り、上記の流れとしている。

### 詳細

1. devcontainer 起動
1. `claude`で claude code 起動
1. GitHub で issue を作る。

   ```
   ## 概要
   ～～を元に、Todoを表示する画面を作成する。

   Todoはまずはハードコードしたデータで実装する。
   ルートは'/'にしてください。'/'にアクセスするとTodo一覧が表示される。

   まずは簡単な実装とvitestによるテストを実装してください。

   playwrightによるe2eテストは現時点では不要。
   ```

1. claude code のコンテキストをクリア（`/clear`）
1. claude code で`/plan-github-issue {イシュー番号}`実行。
   - GitHub に **新しい issue** が作成される。
   - 元の issue は close になる。
1. GitHub で issue を確認する。  
   必要な場合は編集する。
1. claude code で`/fix-github-issue {プランイシュー番号}`
   **イシュー番号が変わっているので注意**  
1. `/clear`する。
1. レビューさせる。`/review-local-changes {番号}`
1. reviews/isuue-{番号}-review.md を確認する。  
   改善点で不要なものがあれば消したり、追加したりする。
1. レビュー反映させる。`/apply-review-feedback {番号}`  
   コミットはされるはず。
1. PR を作る。`/create-pr {番号}`
1. （チームメンバーにレビューをもらう）
1. GitHub でマージする

## Tips

- claude code ベストプラクティスでは TDD が推奨されている。  
  CLAUDE.md で TDD になるよう指示した方がよい。  
  例
  ```
  テスト駆動開発になるように、 @CLAUDE.md を更新してください。
  ```
- CLAUDE.md に記載するオススメ内容。  
  これも CLAUDE.md を修正するように依頼するとよい。
  - テストを必ず実行する
  - linter を必ず通す
