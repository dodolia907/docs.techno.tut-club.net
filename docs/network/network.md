---
title: Network
sidebar_label: Network
sidebar_position: 3
---
# Network
## 概要
ここでは部室のネットワークの全体図を示します。
![network](https://raw.githubusercontent.com/TechnoTUT/Network/main/network.drawio.svg)  
ルーターとしてNEC IX2025、L2スイッチとしてCisco Catalyst 2960+ 24TC-Lを、無線APにはELECOM WRC-1167FEBK-Sを使用しています。  
RekordboxのLink Export機能により、コンピュータで楽曲情報を取得したり、スマートフォンやタブレットでDJを行ったりすることができます。  
さらに、LAN内のWebサーバーにアクセスすることで、楽曲情報を確認したり、[現在のDJの情報](https://currentdj.technotut.net)を確認したりすることができます。

## ポートについて
ポートとvlanの対応は以下の通りです。

```
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/19, Fa0/20
10   DJ-Network                       active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/21, Fa0/22
20   VJ-Network                       active    Fa0/7, Fa0/8, Fa0/9, Fa0/10
                                                Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Gi0/1, Gi0/2
30   Lightning-Network                active    Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/23
```

NDIを使用する場合は、ギガビットポートであるGi0/1, Gi0/2を使用してください。
ポート Fa0/19, Fa0/20 は、トランクポートとして設定されています。コンピュータを接続し、VLAN IDを指定することで、指定したVLANに接続することができます。

### VLAN IDの指定方法
NIC(ネットワークインターフェースカード)のメーカーによって、VLAN IDの指定方法が異なります。以下では、RealtekとIntelのNICを使用している場合の設定方法を示します。  
#### RealtekのNICを使用している場合
RealtekのNICを使用している場合は、以下の手順でVLAN IDを指定することができます。  
1. Realtek社の公式サポートページから、Realtek Ethernet Diagnostic Utilityをダウンロードしインストールします。  
2. Realtek Ethernet Diagnostic Utilityを起動します。  
3. 一番左で目的のNICを選択(Realtek USB GbE Family Controller など)し、`VLAN`タブを選択します。  
4. `追加`を選択し、VLAN IDを入力します。追加したいVLANが複数ある場合は、必要なVLAN IDをすべて追加します。  
5. 変更は即時反映されます。うまくいかない場合は、コンピュータを再起動してみてください。それでもうまくいかない場合は、管理者にご相談ください。  
6. もとに戻す場合は、`削除`を選択し、VLAN IDをすべて削除します。  

#### IntelのNICを使用している場合
IntelのNICを使用している場合は、以下の手順でVLAN IDを指定することができます。  
1. Intel社の公式サポートページから、Intel PROSetをダウンロードしインストールします。(Windows 11には対応していません。)  
2. 管理者権限でIntel PROSetを起動します。  
3. 左メニューで目的のNICを選択(Intel(R) Ethernet Connection I219-V など)し、`チーム化/VLAN`タブを選択します。  
4. `新規作成`を選択し、VLAN IDを入力します。追加したいVLANが複数ある場合は、必要なVLAN IDをすべて追加します。  
5. 変更は即時反映されます。うまくいかない場合は、コンピュータを再起動してみてください。それでもうまくいかない場合は、管理者にご相談ください。  
6. もとに戻す場合は、`削除`を選択し、VLAN IDをすべて削除します。  

## 設定の変更について
### 固定IPアドレスの設定
固定IPアドレスを設定するには、以下の手順を行ってください。  
1. ルーターに接続します。TeraTermなどで部室の無線LANまたはDJネットワークに接続し、`192.168.100.1`にSSHします。(VJのネットワークに接続している場合は、`172.16.0.1`に接続します。)  
2. ルーターにログインします。ユーザー名は`admin`、パスワードは`admin`です。  
3. `enable-config`コマンドを実行して、グローバルコンフィグモードに移行します。  
4. `show ip dhcp profile vj`コマンドを実行して、現在のVJネットワークのDHCPプロファイルを確認します。  
5. `ip dhcp profile vj`コマンドを実行して、VJネットワークのDHCPプロファイルを選択します。  
6. `fixed-assignment [IPアドレス] [MACアドレス]`コマンドを実行して、固定IPアドレスを設定します。このとき、`show ip dhcp profile vj`コマンドで確認したIPアドレスと新たに設定するIPアドレスが重複しないように注意します。また、設定を誤り消去したい場合は、`no fixed-assignment [IPアドレス]`コマンドを実行してください。  
7. 変更は即時反映されます。問題がなさそうでしたら、`exit`コマンドでグローバルコンフィグモードに戻り、`write memory`コマンドで設定を保存します。  

### VLANの変更
CiscoスイッチのVLAN割当を変更するには、以下の手順を行ってください。  
1. Ciscoスイッチに接続します。TeraTermなどで部室の無線LANまたはDJネットワークに接続し、`192.168.100.3`にSSHします。(VJのネットワークに接続している場合は、`172.16.0.2`に接続します。)  
2. Ciscoスイッチにログインします。ユーザー名は`admin`、パスワードは`admin`です。  
3. `enable`コマンドを実行して、特権モードに移行します。  
4. `show vlan`コマンドを実行して、現在のVLANの状態を確認します。  
5. `show startup-config`コマンドを実行して、現在の設定を確認します。  
6. `configure terminal`コマンドを実行して、グローバルコンフィグモードに移行します。  
7. `interface  fastethernet 0/[ポートの番号]`コマンドを実行して、ポートを選択します。複数のポートを同時に変更したい場合は、`interface range fastethernet 0/ポートの番号(はじめ)]-[ポートの番号(おわり)]`コマンドを実行して、ポートを選択します。  
8. 既存の設定を削除します。手順5の出力結果を参考にしながら、`no switchport access vlan`コマンドを実行して、アクセスポートのVLANを削除します。`no switchport trunk allowed vlan`コマンドを実行して、トランクポートのVLANを削除します。  
9. VLANを一つのみ割り当てて通常のスイッチのように使いたい場合は`switchport mode access`コマンドを実行して、アクセスポートに設定します。VLANを複数割り当てて複数のネットワークに所属できるトランクポートとして使いたい場合は、`switchport mode trunk`コマンドを実行して、トランクポートに設定します。  
10. アクセスポートの場合は、`switchport access vlan [VLANの番号]`コマンドを実行して、VLANを割り当てます。トランクポートの場合は、`switchport trunk allowed vlan [VLAN番号]`コマンドを実行して、許可するVLANを割り当てます。  
11. 変更は即時反映されます。`show vlan`コマンドを実行して、VLANの状態を確認します。  
12. 問題がなさそうでしたら、`exit`コマンドで特権モードに戻り、`write memory`コマンドで設定を保存します。  