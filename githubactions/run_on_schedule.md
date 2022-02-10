# Github Actions のスケジュール実行

以下のように記述する。

```yaml
name: Build

on: s
  schedule:
    - cron:  '0 0 * * *'
```

https://docs.github.com/ja/actions/using-workflows/events-that-trigger-workflows#schedule

```
POSIX クーロン構文を使用して、特定の UTC 時間にワークフローを実行できるようスケジュール設定できます。 スケジュールしたワークフローは、デフォルトまたはベースブランチの直近のコミットで実行されます。 スケジュールされたワークフローを実行できる最短の間隔は、5 分ごとに 1 回です。

この例では、ワークフローは毎日UTCの5:30と17:30にトリガーされます。

on:
  schedule:
    # *はYAMLにおける特殊文字なので、この文字列はクオートしなければならない
    - cron:  '30 5,17 * * *'
```

```
クーロン構文では、スペースで分けられた 5 つのフィールドがあり、各フィールドは時間の単位を表わします。

┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12 or JAN-DEC)
│ │ │ │ ┌───────────── day of the week (0 - 6 or SUN-SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

