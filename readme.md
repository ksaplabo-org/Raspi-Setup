# Raspbeery Pi OSインストール方法  
## OSのインストール方法
- Raspberry Piに使用するSDカードを自分のPCに接続  

- インストーラを以下のURLからダウンロードする。  
https://www.raspberrypi.com/software/  
<img alt="OSインストーラ画像" src="./img/OSインストールページ.png" width="700" height="400">  

- ダウンロードしたインストーラ（imager_1.7.1.exe）を起動し、インストールを行う。
- Raspberry Pi Imagerが起動したら、「CHOOSE OS」をクリック。  
<img alt="OSインストーラ画像" src="./img/OS%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%A9.png" width="300" height="200">

- 「Operating System」から一番上を選択。  
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 103252.png" width="300" height="200">

- 次に「Storage」を選択。  
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 104434.png" width="300" height="200">

- PCに接続したSDカードを選択。  
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 104702.png" width="300" height="200">

- 「WRITE」を選択して、書き込みを行う。(10分ほど掛かります)  
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 105111.png" width="300" height="200">
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 105257.png" width="300" height="200">

## Wifi設定の手順
- SDカードに書き込みが終わった後、（今回は）Dドライブ直下に「ssh」という空のファイルを新規作成。  
<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 110757.png" width="300" height="200">  

- 同様のディレクトリにテキストを新規作成し、内容を編集し「wpa_supplicant.conf」という名前で保存。編集内容は以下の通り  

```  
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=JP

network={
        ssid="1つ目のSSID"
        psk="1つ目のSSIDのパスワード"
        key_mgmt=WPA-PSK
}  
```

<img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-28 111544.png" width="300" height="200">  

## Raspberry Pi OS設定  
- 上記の手順が終われば、自分のPCからSDカードを抜いて、Raspberry PiにSDカードを入れる。   
- Raspberry Piの電源をつける。 
- Raspberry PiのIPアドレスを調べる。  
【参考：Raspberry PiのIPアドレスの調べ方】  
 確実にIPアドレスがわかる方法が確立していないため、例としていくつか紹介します。
  - Windowsのコマンドプロンプトから「arp -a」を実行すると  
  　同一セグメント内に存在するIPアドレス-物理アドレスの一覧が表示されるため  
    <img alt="OSインストーラ画像" src="./img/スクリーンショット 2022-03-29 095453.png" width="300" height="200">  

    その中からRaspberry PiのIPアドレスを推測する。（pingを使うとか...）  
  　※arp -aでIPアドレスがRaspberry PiのIPアドレスが出てこないことがあります。  
  - RaspbBerry Piの電源をつけ、ディスプレイと接続しIPアドレスを直接調べる。  
    今のところこのやり方のほうが確実です。
  　
    
    
    
    43.125

  - 自分のネットワークから接続しているIPアドレスを調べるコマンド  
   コマンドプロンプトで　arp -a
- テラタームからSSHで接続出来たら
　sudo raspi-config　でVNCを有効化する
- VNCviwerからラズパイにはいり、OＳセットアップを行う。  
  - set Country
  - ソフトウェアのアップデートは行う
  - VNCが遅いときの対応方法がTeamsの記事にある  
- ここまで来たらあとは手順書
