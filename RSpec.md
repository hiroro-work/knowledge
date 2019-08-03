# RSpec

## Systemテスト

### 範囲を絞ってボタン/リンクをクリック
```
within(...) do
  click_on 'ボタン/リンク'
end
```

### fill_inで正規表現
```
fill_in with: 'hoge', id: \regexp\
```
