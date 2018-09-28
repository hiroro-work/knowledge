# Heroku

## master以外のブランチをHerokuにデプロイ
```
$ heroku login  
$ git push heroku {branch name}:master
```

## デプロイ時に自動でdb:migrate
```
Procfileに "release:" 行を追加して自動実行したいコマンドを設定

$ cat Procfile
release: rails db:migrate
```
