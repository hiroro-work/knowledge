# Rails Knowledge

## rails new

### Postgresqlを指定してアプリ作成
```
$ rails new appname -d postgresql
$ rails db:create

※ rails db:createを行わず手動でDB作成する場合は以下
$ sudo -u postgres psql
$ postgres=# CREATE DATABASE appname_development;
$ postgres=# CREATE DATABASE appname_test;
$ postgres=# \q
```

## rails generate

### model

### scaffold

### カラム追加
```
$ rails g migration AddColumnTo{Model名} {カラム} 
```

### モデル削除
```
$ rails g migration Drop{Model名}
```

## rails db

### testDBのmigrate
```
$ rails db:migrate RAILS_ENV=test
```

### DB初期化
```
$ rails db:migrate:reset
```

## locales

### locales配下のサブディレクトリ配置したymlファイルを読み込む
```
application.rbに★の行を追加

module XXXXX
  class Application < Rails::Application
    ～
    config.i18n.load_path += Dir[Rails.root.join('config', 'locales', '**', '*.{rb,yml}').to_s] ★
    ～
  end
end
```

## gem

### bundle install前のnokogiri事前設定
```
$ sudo yum install libxml2-devel libxslt-devel
$ bundle config --local build.nokogiri --use-system-libraries
```
