# Alexa Hostedされているスキルをローカルでダイアログのテスト

ask cliにプロファイル設定をする。

```bash
$ ask configure --profile { my profile }
```

ソースコードをDLする。

```bash
$ ask init --hosted-skill-id { skill id } --profile { my profile }
```

(プロファイルがdefaultではないため？)

`ask-resources.json` が `.gitignore` されているため、DLしたソースコードには `ask-resources.json` が含まれていない。

そのため `get-skill-manifest` でask-resources.jsonを作成する。

```bash
$ ask smapi get-skill-manifest --skill-id { skill id } --profile { my profile } > ask-resources.json
$ ask dialog --profile { my profile }
```

