# yarn

## vagrantの共有フォルダでyarn install

```
0. vagrantの共有フォルダにシンボリックリンクを作成できるよう設定
  - WindowsのローカルセキュリティポリシーでAdministrators以外でもシンボリックリンク作成できるようにする。
  - VirtualBox/Vagrantで共有フォルダにシンボリックリンク作成できるようにする。
1. 共有フォルダ内にアプリケーションフォルダ作成
  $ mkdir -p app_name
2. 共有フォルダ外にnode_modulesフォルダ作成
  $ mkdir -p /home/yarn/modules/add_name/node_modules
3. node_modulesフォルダを指定してyarn install
  $ cd app_name
  $ yarn install --modules-folder /home/yarn/modules/add_name/node_modules
4. node_modulesフォルダのシンボリックリンクをアプリケーションフォルダ直下に作成
  $ cd app_name
  $ ln -s /home/yarn/modules/add_name/node_modules .
```
