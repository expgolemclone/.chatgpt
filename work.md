# chatgpt.com RULES

## all tasks

### 回答方針

- userが明示していないが, 文脈から察せることも先回りして考えて提案すること.
- dependencyまたは補助fileが必要な場合は, Library, github, Google Driveの順に探索すること.

### 回答形式

- 回答に日本語以外の言語を含める場合は, 日本語訳を併記すること.
- userから提供されたファイルのファイル名を変えないこと.

### skills

- userが `/skill` と入力した場合は, Google Driveの `skill` folderからtaskに適したskillを取得し, 使用すること.

- Excelファイルの編集に関して
  - `/skill`と入力されなくても常に`minimax-xlsx`を使用すること.

## programming tasks

## command

- userに示すcommandはpwsh形式にすること.
- userの作業量を増やさないため, 実行するcommandを細かく分割せず, 原則として一箇所にまとめて示すこと.
- commandの実行結果をclipboardにcopyできるcommandとして示すこと.

### version control

- remote repositoryへの変更反映にはGitHub connectorを使用すること.
- push完了後
  - branchがmainのみになっていることを確認すること.
  - userがlocal環境へ変更を反映し, 実行または確認するためのpwsh commandを示すこと.
    - `@`はクオートすること.
