# ラズパイインストール方法  


- OSを書き込むためのソフト  
https://www.raspberrypi.com/software/  
[url](https://www.raspberrypi.com/software/)   

```
インストール→実行   
```
<img alt="OSインストーラ画像" src="./img/OS%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%A9.png" width="300" height="200">

```
CHOOSE OS→一番上→Strage→選択→Write  
```  

- SDカードに書き込みが終わった後  
  - sshという空のファイルをDドライブ直下に作成
  - wpa_supplicant.confを編集して、使用するWi-fiのSSIDとPWを入力し、Dドライブ直下におく  
- 出来たらラズパイにSDカードを入れて電源をつける
- ラズパイのIPアドレスを調べる  
  - 自分のネットワークから接続しているIPアドレスを調べるコマンド  
   コマンドプロンプトで　arp -a
- テラタームからSSHで接続出来たら
　sudo raspi-config　でVNCを有効化する
- VNCviwerからラズパイにはいり、OＳセットアップを行う。  
  - set Country
  - ソフトウェアのアップデートは行う
  - VNCが遅いときの対応方法がTeamsの記事にある  
- ここまで来たらあとは手順書

# DynamoDBで通知してからまでの流れ  
- （RaspberryPi）温度・湿度センサー環境の作成  
→基本は手順書通り。特につまずいてはいない
- （AWS）IoT Coreで「モノ」情報を作成  
→右上の作業領域を東京にすることを忘れないように  
→証明書のダウンロードでつまずくことがあった  
エンドポイント、ROOTCA→証明書を発行している大元、CERT→証明書、PRIKEY→privatekey  
→トピック名はIotCoreの掲示板みたいなもので、そこからSelectしてDynamoDBにデータを入れる  
- ファイル転送のツール　WinSCP
- 低階層のパイソンから実行し、Lamda関数はAWS上にある、zipファイルはそこから転送する。  
-  
- lambda関数からEC2に設定するとき  
  - 手順からLambdaがどのVPC内に設置されるかの設定が抜けている  
  - EC2のIPアドレスを指定するIPアドレスが、EC2のグローバルIPアドレスを指定していた  
  vsCodeのPostではうまくいくが、Lambdaからはうまくいかない
  - VSCodeでJSONを作るときは、’ではなく、”を使う
- 変更テスト