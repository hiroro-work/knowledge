# Xvfbで仮想ディスプレイ環境構築

1. ロケールを日本語に変更
```
$ sudo yum update -y
$ sudo yum reinstall -y glibc-common
$ localectl set-locale LANG=ja_JP.UTF-8
$ source /etc/locale.conf
$ sudo localectl set-keymap jp106
```

2. Xvfbインストール
```
$ sudo yum install -y Xvfb
$ sudo vi ~/.bash_profile
DISPLAY=:1 ★
PATH=$PATH:$HOME/.local/bin:$HOME/bin

export DISPLAY ★
export PATH
```

3. Chromeインストール（Chrome使いたい場合）
```
$ sudo vi /etc/yum.repo.d/google-chrome.repo
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
$ sudo yum install -y google-chrome-stable
```

4. 日本語フォントインストール
```
$ sudo yum install -y vlgothic-fonts vlgothic-p-fonts
```

5. Xvfb起動
```
$ Xvfb :1 -screen 0 1024x768x24 > /dev/null &
```
