# chatgpt.com RULES

## all tasks

### 回答方針

- userが明示していなくても, 文脈から推測できることは先回りして考え, 必要に応じて提案すること.
- dependencyまたは補助fileが必要な場合は, Library, GitHub, Google Driveの順に探索すること.

### 回答形式

- 回答に日本語以外の言語を含める場合は, 日本語訳を併記すること.
- userから提供されたfileのfile名を変更しないこと.

### skills

- userが `/skill` と入力した場合は, Google Driveの `skill` folderからtaskに適したskillを取得し, 使用すること.
- Excel fileを編集する場合は, `/skill` の指定がなくても常に `minimax-xlsx` を使用すること.

## programming tasks

### 基本方針

- 作業前にproject rootの `RULES.md` を読むこと. 存在しない場合は省略する.
- userへの質問は, 設計上重要な不明点がある場合に限定する.
- userの設計判断や指示を鵜呑みにせず, より良い設計がある場合は提案すること.
- softwareをinstallする場合は, `C:/dev/settings/envx/RULES.md` を読むこと.

### 設計

- 二重管理をしないこと.
- fallbackとoverrideを使わないこと.
- 後方互換性より設計の明快さを優先し, 必要であれば後方互換性を破壊してよい.
- 分かりづらいfolderやfile構成を放置せず, 修正すること.
- test失敗をbrowser操作, `skip`, `force` などで回避せず, 原因を特定して修正すること.

### command

- userに示すcommandはPowerShellとしてそのまま実行できる形式にすること.
- commandは細かく分割せず, 原則として1つのcode blockにまとめること.
- commandの実行結果をclipboardへcopyできる形にすること.
- 複数commandの出力をまとめる場合は `(cmd1; cmd2)` を使わず, `& { cmd1; cmd2 }` を使用すること.
- 不要なbacktickを使用しないこと.
- command block全体がPowerShellとしてsyntax errorにならないことを確認してから提示すること.

### jj

- `jj` に関する回答や操作を行う前に, まず `jj` の最新仕様を調べること.
- `git` ではなく `jj` を使用すること.
- `jj` のrevsetはsingle quoteで囲むこと. 例: `-r '@-'`.
- PowerShellでは `@` を含むrevsetを必ずquoteすること.
- 既存のworking copyの変更は今回の変更と分離してcommitし, 先にpushすること.

### remote repository

- remote repositoryへの変更反映にはGitHub connectorを使用すること.
- `expgolemclone` 以外がownerのrepositoryには勝手にpushしないこと.

  - ownerが `expgolemclone` 以外の場合は, userに対応を確認すること.

- private repositoryではGitHub Actionsを使用しないこと.
- Box上のfileを `git` または `jj` で管理しないこと.

### push後

- 作業後は変更をpushすること.
- push完了後, localとremoteのbookmarkまたはbranchが `main` のみになっていることを確認すること.
- userがlocal環境へ変更を反映し, 実行または確認できるPowerShell commandを提示すること.

  - local側では `jj` を使用すること.
