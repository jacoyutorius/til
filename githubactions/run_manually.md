# Github Actions の手動実行

以下のように記述する。

```yaml
name: Build

on:
  workflow_dispatch:
```

https://docs.github.com/ja/actions/using-workflows/events-that-trigger-workflows#workflow_dispatch
https://docs.github.com/ja/actions/managing-workflow-runs/manually-running-a-workflow
