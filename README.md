# create-kind-on-virtualbox
本ツールは1コマンドでkindを自動構築するツールです。

## 動作確認バージョン
以下の環境でツールが動作することを確認しています。
- ローカルPC : windows10
- Vagrant : 2.4.1
- VirtualBox : 7.0.20
- kind : 0.24.0        ※kubernetes: 1.31
- Rocky Linux : 8.x    ※cpu : 2, memory : 4GB

## 手順

### 1. 事前準備
ツール動作に必要なコンポーネントをインストールする。

1. VirtualBoxのインストール  
[VirtualBox 公式サイト ダウンロードページ](https://www.virtualbox.org/wiki/Downloads)にアクセスし、インストーラーをダウンロードする。その後、インストールを行う。

2. Vagrantのインストール
[Vagrant 公式サイト ダウンロードページ](https://developer.hashicorp.com/vagrant/install?product_intent=vagrant)にアクセスし、インストーラーをダウンロードする。その後、インストールを行う。

3. Gitのインストール
[Git 公式サイト ダウンロードページ](https://gitforwindows.org/)にアクセスし、インストーラーをダウンロードする。その後、インストールを行う。

### 2. 資材のclone
[github](https://github.com/yohe-lab/create-kind-on-virtualbox)から資材をcloneする。
```
> git clone https://github.com/yohe-lab/create-kind-on-virtualbox.git
```

### 3. (必要に応じて)設定ファイルの変更
- Vagrantfile：ノードリソースやホスト名など
- Ansiblefile：追加処理など

### 4. VM～kindクラスタ作成(vagrantコマンドの実施)
vagrantコマンドを用いて、ツールを実行する。
```
> cd create-kind-on-virtualbox
> vagrant up
```

## デモ




## 初期パラメータ

### vagrantfile  

<table border="1">
  <tr>
    <th>key</th>
    <th>value</th>
  </tr>
  <tr>
    <td>box</td>
    <td>bento/rockylinux-8</td>
  </tr>
  <tr>
    <td>hostname</td>
    <td>kind-0</td>
  </tr>
    <tr>
    <td>ip</td>
    <td>10.240.0.30</td>
  </tr>
    <tr>
    <td>cpu</td>
    <td>2</td>
  </tr>
    </tr>
    <tr>
    <td>memory</td>
    <td>4096</td>
  </tr>
</table>

### ansible(main.yml)
<table border="1">
  <tr>
    <th>key</th>
    <th>value</th>
  </tr>
  <tr>
    <td>kind_version</td>
    <td>0.24.0</td>
  </tr>
  <tr>
    <td>kubectl_version</td>
    <td>1.31</td>
  </tr>