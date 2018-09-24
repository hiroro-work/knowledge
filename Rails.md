# Rails Knowledge

## rails generate

### model

### scaffold

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
