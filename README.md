# setup-my-lubuntu

[Lubuntu](https://lubuntu.me/) 向けのセットアップスクリプト。
21.10 で動作確認。


## 事前準備

1. ansible 向けに sudo 実行時のパスワード入力を無効化。

```bash
cd /etc; pwd
echo "%$(id -ng) ALL=(ALL) NOPASSWD: ALL" | sudo tee sudoers.d/$(id -ng)
```

2. 再ログインする。
3. 初期 apt ミラーは遅いので, 国内ミラーに変更。
   * 2021-11-10 時点で, ftp.iij.ad.jp は一部で 404 が返却されるため, 利用できない。

```bash
cd /etc/apt; pwd
sudo sed -i -e 's|archive\.ubuntu\.com|ftp.riken.jp/pub/Linux|g' sources.list
sudo apt clean
sudo apt update
sudo apt -y install ansible
```


## 実行

```bash
ansible-playbook site.yml -i hosts.yml
```


## インストール先

* AWS CLI
   * `/usr/local/bin/aws`
* Terraform
   * `/bin/terraform`
* Poetry
   * `~/.poetry/bin/poetry`
* Serverless Framework
   * `~/.serverless/bin/serverless`


どっとはらい。
