# webpackerの導入

既存のRailsプロジェクトにwebpackerを導入するには

```
既存のプロジェクトにWebpackerを追加するには、
プロジェクトのGemfileにwebpacker gemを追加してbundle installを実行し、続いてbin/rails webpacker:installを実行します。 
```

**Gemfile**

```
gem "webpacker" # 追加
```

```
vscode ➜ /workspace (webpacker ✗) $ bundle

Fetching webpacker 5.4.3
Installing webpacker 5.4.3
Bundle complete! 16 Gemfile dependencies, 77 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

**webpacker:install** を実行する

```bash
vscode ➜ /workspace (webpacker ✗) $ bin/rails webpacker:install
      create  config/webpacker.yml
Copying webpack core config
      create  config/webpack
      create  config/webpack/development.js
      create  config/webpack/environment.js
      create  config/webpack/production.js
      create  config/webpack/test.js
Copying postcss.config.js to app root directory
      create  postcss.config.js
Copying babel.config.js to app root directory
      create  babel.config.js
Copying .browserslistrc to app root directory
      create  .browserslistrc
The JavaScript app source directory already exists
       apply  /usr/local/bundle/gems/webpacker-5.4.3/lib/install/binstubs.rb
  Copying binstubs
       exist    bin
      create    bin/webpack
      create    bin/webpack-dev-server
      append  .gitignore
Installing all JavaScript dependencies [5.4.3]
         run  yarn add @rails/webpacker@5.4.3 from "."
yarn add v1.22.17
info No lockfile found.
[1/4] Resolving packages...
〜
Done in 32.50s.
Webpacker successfully installed 🎉 🍰
vscode ➜ /workspace (webpacker ✗) $ 
```

## webpacker:installで追加されるファイル

```bash
$ git status
On branch webpacker
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   .gitignore
	modified:   Gemfile
	modified:   Gemfile.lock
	modified:   db/seeds.rb

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.browserslistrc
	babel.config.js
	bin/webpack
	bin/webpack-dev-server
	config/webpack/
	config/webpacker.yml
	package.json
	postcss.config.js
	yarn.lock

no changes added to commit (use "git add" and/or "git commit -a")
```

## JavaScriptをWebpacker経由で利用する

```
app/javascript/packsディレクトリ以下のJavaScriptファイルがコンパイルされて独自のpackファイルにまとめられます。
```

`packs/javascript` を作成。

```bash
vscode ➜ /workspace (webpacker ✗) $ mkdir app/javascript/packs
vscode ➜ /workspace (webpacker ✗) $ touch app/javascript/packs/application.js
```

## refs 

https://railsguides.jp/webpacker.html