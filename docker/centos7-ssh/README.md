# centos7-ssh

## TL;DR

- centos7のコンテナに`root`で`ssh`できる基本構成
- `docker port {コンテナ名} 22`コマンドで、ホスト向けに空いているポート番号を確認できる

## コマンド実行例

```shell
// イメージ作成
$ docker build -t centos7_ssh .

// バックグラウンドでコンテナを起動
$ docker run -d -P --name test_ssh centos7_ssh

// ポート確認
$ docker port test_sshd 22

0.0.0.0:33402

// ssh接続確認
$ ssh root@localhost -p 33402
```
