# Raspbeery Pi OSインストール方法  


- OSを書き込むためのソフトを以下のURLからインストールする。  
https://www.raspberrypi.com/software/  
<img alt="OSインストーラ画像" src="./img/OSインストールページ.png" width="400" height="200">

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
