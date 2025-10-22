# Tutorial

## 目次
1．[これは何?](#1-これは何)  
2．[大前提として…](#2-大前提として)  
3．[Git のインストールと設定](#3-git-のインストールと設定)  
 3.1．[インストール](#31-インストール)  
 3.2．[初期設定](#32-初期設定)  
4．[Python のインストール](#4-python-のインストール)  

## 1. これは何?
`Git` と `Python` のインストール説明をします。

---

## 2. 大前提として…
以下を要求します。
- OS : Windows
- 日本語やスペースのないアカウント名の Windows アカウント
- 管理者権限が使えること
- GitHub のアカウント（無料）を持っていること

---

## 3. Git のインストールと設定
### 3.1. インストール
ターミナルを開き、以下を実行してください。
```PowerShell
> winget install --id Git.Git --override "/VERYSILENT"
```

インストール終了後、以下を実行して、インストールされていることを確認してください。
```PowerShell
> git --version
```

`git version ...` のように表示されれば成功です。

### 3.2. 初期設定
ユーザ情報の登録を行います。ターミナルで以下を順に実行してください。  
ユーザ名とメールアドレスをダブルクォーテーション(`"`)で挟むことに注意してください。
```PowerShell
> git config --global user.name "GitHub ユーザー名"
> git config --global user.email "GitHub 登録メールアドレス"
```

次に ssh キーを生成します。以下を実行してください。
```PowerShell
> ssh-keygen -t ed25519 -C "GitHub 登録メールアドレス"
```
Enter を3回押してデフォルト保存します。以下を実行し、公開鍵を表示します。
```PowerShell
> type $env:USERPROFILE\.ssh\id_ed25519.pub
```
表示された公開鍵をコピーしてください。その後、<https://github.com/> にアクセスしてください。  
以下の順にページを遷移させてください。  
右上のユーザアイコン -> `Settings` -> 左のメニューバーから `SSH and GPG keys` -> `New SSH key`  
Title は適当につけ、key の枠に先ほどコピーしたものをペーストし `Add SSH key`

ターミナルに戻り、以下を実行します。
```PowerShell
> ssh -T git@github.com
```
`Hi! ユーザ名` のように表示されれば成功です。  

#### （推奨）メールアドレスの秘匿設定
GitHub のプライバシー保護を維持したまま push するには noreply アドレスを使います。  
これは以下の手順で設定できます。

1. <https://github.com/settings/emails> を開きます．
2. 「Keep my email addresses private」にチェックを入れたまま、表示されている `12345678+username@users.noreply.github.com` のようなアドレスをコピーします。
3. ターミナルで以下を実行します．
```PowerShell
> git config --global user.email "12345678+username@users.noreply.github.com"
```
これでプライベートメールアドレスは公開されません。  
以上で Git のインストールおよび設定は終了です。

---

## 4. Python のインストール
Python 3.13 系で最新のものを用いれば十分だと思います。  
ターミナルで以下を実行してください。
```PowerShell
> winget install --id Python.Python.3.13 -e --source winget
```
3.13 系で最新の Python （2025-10-21 時点で 3.13.9）をインストールできます。  
以上で Python のインストールは終了です。

---
Copyright © 2025 pantsman