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
```
$ rails g model {Model名} {カラム:データ型} ...

[データ型]
string 文字列型
text テキスト（不定長文字列）型
integer 整数型
float 浮動小数点数型
decimal 固定長整数型
datetime 日時型
timestamp タイムスタンプ型
time 時刻型
date 日付型
binary バイナリ文字列型
boolean 真偽値型
references 他テーブルへの外部キー
```

### scaffold

### migration

#### カラム追加
```
$ rails g migration AddColumnTo{Model名} {カラム}:{データ型} 
```

#### モデル削除
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

### 特定VERSIONのみmigrate
```
$ rails db:migrate:status
$ rails db:migrate:up VERSION={Migration ID}
```

## rails spec

### RSpec実行
```
$ rails spec
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

## webpack

### stimulus
```
$ rails webpacker:install
$ rails webpacker:install:stimulus
$ vi app/views/layouts/application.html.haml
!!!
%html
  %head
    ～
    = javascript_pack_tag 'application'
    ～
```

## gem

### bundle install前のnokogiri事前設定
```
$ sudo yum install libxml2-devel libxslt-devel
$ bundle config --local build.nokogiri --use-system-libraries
```
vagrantで共有フォルダを使ってる場合はそれでもダメっぽいので、  
その時は以下のように共有フォルダ外にインストールされるようにする。
```
$ mkdir -p ~/rails/vendor/bundles/プロジェクト名
$ bundle install --path ~/rails/vendor/bundles/プロジェクト名
```

### path指定せずにインストールしたgemを一括削除
```
$ gem uni -aIx $(gem li --no-versions | grep -v -E "rdoc|psych|io-console|bigdecimal|rake|json|zlib|webrick|strscan|stringio|sdbm|scanf|openssl|ipaddr|fileutils|fiddle|fcntl|etc|date|csv|cmath")
```
