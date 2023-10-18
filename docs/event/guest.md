---
title: ゲストのみなさまへ
sidebar_label: ゲストのみなさまへ
sidebar_position: 1
---
# ゲストのみなさまへ
Last update: 2023/10/4 by DDlia   

ここでは技科大祭2023 コモンズイベントでの注意事項等を記載します。  
※この情報は2023年10月4日現在の情報です。機材トラブル等により変更になる可能性があります。  

## 会場内について
会場内は演出に用いる各種配線がされています。養生テープ等で固定していますが、踏んだり引っ掛けたりしないよう注意をお願いいたします。特に、電源ケーブルや通信ケーブルが切れたり不安定になったりすると音や光、映像が停止することがあります。  
荷物置き場等の控え場所は別途連絡します。貴重品は各自での管理をお願いします。また、控え場所には様々な機器が置いてありますので飲み物等の取り扱いには十分注意をお願いします。  

## DJ機器について
DJ機器は[XDJ-XZ](https://www.pioneerdj.com/ja-jp/product/all-in-one-system/xdj-xz/black/overview/)を使用します。USBメモリまたはPRO DJ LINK(後述)による曲の読み込みをサポートしています。  
ゲイン情報については、当日ご連絡いたします。  
また、ロードミスを防ぐため、再生中のデッキには曲をロードすることができない設定に変更しております。曲を読み込む場合は対象のデッキの再生を停止してから読み込みをお願いいたします。

### PRO DJ LINKについて
[XDJ-XZ](https://www.pioneerdj.com/ja-jp/product/all-in-one-system/xdj-xz/black/overview/)はPCとLANケーブルで接続することで曲の読み込みができるPRO DJ LINKに対応しています。以下の手順で操作を行うことで、USBメモリに書き出すことなくPCから直接曲を読み込ませることが可能です。  
1. Rekordboxを起動
2. PCとDJブースのLANケーブルを接続  
※自動でWeb認証画面が表示されますが、無視していただいて構いません。認証なしでDJ機器とのみ通信する仕様となっています。
3. RekordboxをEXPORTモードに変更  
(左上のPERFORMANCE、EDIT、LIGHTNINGのいずれかの表示となっているところをEXPORTに変更)
4. 左下に`LINK`というボタンが現れるので、選択
5. XDJ-XZのRekordboxボタンから、もしくはPCを操作し下側の部分にドラッグアンドドロップを行う  

なお、DJブースのLANケーブルを接続してもインターネットに接続することはできません。インターネット環境が必要な場合はスマートフォンとのテザリングやモバイルルータ等をご利用ください。  
豊橋技術科学大学構成員であればtutwifiもしくはeduroam、名古屋大学等のeduroam参加機関の構成員であればeduroamを利用できます。詳細につきましては、以下をご覧ください。  
[無線LAN | 豊橋技術科学大学 情報メディア基盤センター](https://imc.tut.ac.jp/network/wlan.html)  
[eduroam JP | 豊橋技術科学大学 情報メディア基盤センター](https://imc.tut.ac.jp/network/eduroam.html)  
[名古屋大学構成員向け eduroam JP 認証サービス利用方法 | 名古屋大学 情報連携推進本部](https://icts.nagoya-u.ac.jp/ja/services/eduroam/)  

## VJ機器について
VJ用プロジェクターへの映像出力にはVJブースのHDMIケーブルをご利用ください。VJ転換時にはOBSを利用したソフトウェアベースのVJスイッチを利用します。

### VJスイッチ(OBS)の使い方
![fig1](https://cdn.discordapp.com/attachments/982839912887877716/1159126777277464676/image.png?ex=651ec06f&is=651d6eef&hm=a71d386160b6126c5411134f0852f9f0d783db6005324c6e8a5b4f70244a88b2&)  
画面左側がプレビュー画面、画面右側がプログラム画面(プロジェクターに映っているものと同じもの)となっています。  
左下のシーンから`HDMI入力`を選択し、プレビュー画面とプログラム画面との間のトランジションを押すと、プレビュー画面の内容(HDMI入力)をプログラム画面に反映することができます。

### Ableton Linkについて
VJブースのLANケーブルを接続することで、Ableton Linkを利用できます。 Ableton Linkを利用することで、VJソフトウェアのBPMをDJのBPMに自動追従させることができます。  
Resolume Avenueでの利用方法を以下に示します。  
1. VJブースのLANケーブルをPCに接続  
2. Resolume Avenueを起動
3. Resolume Avenueの`LINK`を選択  
(`LINK`ボタンが無い場合は、`表示`> `Ableton Linkを表示` の順で選択すると`LINK`ボタンが現れます)  

※注意 BPMの自動追従はDJ機器のグリッド情報に基づいています。DJが事前にグリッドを調整していない場合はビートがズレたり、BPMが合わない可能性があります。

### NDIについて
VJブースのLANケーブルを接続することで、NDIを利用できます。 NDIはIPネットワークを用いて映像伝送を行うプロトコルであり、技科大祭ではVJ映像やカメラの映像伝送に用いています。  
NDIを利用することで、VJパフォーマンスにDJ手元のカメラ映像を取り込むといったことが可能です。以下、Resolume Avenueでの利用方法です。  
1. VJブースのLANケーブルをPCに接続  
2. Resolume Avenueを起動  
3. Resolume Avenue右側のSourcesタブを開く
4. Sourcesタブ下側、NDI SERVERS内の任意の映像をCompositionにドラッグアンドドロップする  
`localhost(cam1)`を取り込むと、DJ手元の映像を取り込むことが可能です

なお、VJブースもDJブース同様にLANケーブルを接続してもインターネットに接続することはできません。インターネット環境が必要な場合はスマートフォンとのテザリングやモバイルルータ等をご利用ください。  
豊橋技術科学大学構成員であればtutwifiもしくはeduroam、名古屋大学等のeduroam参加機関の構成員であればeduroamを利用できます。詳細につきましては、以下をご覧ください。  
[無線LAN | 豊橋技術科学大学 情報メディア基盤センター](https://imc.tut.ac.jp/network/wlan.html)  
[eduroam JP | 豊橋技術科学大学 情報メディア基盤センター](https://imc.tut.ac.jp/network/eduroam.html)  
[名古屋大学構成員向け eduroam JP 認証サービス利用方法 | 名古屋大学 情報連携推進本部](https://icts.nagoya-u.ac.jp/ja/services/eduroam/)  