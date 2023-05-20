---
title: Network
sidebar_label: Network
sidebar_position: 7
---
# Network
Last update: 2023/5/21 by DDlia  
--- 

## 概要
ここでは部室のネットワークの全体図を示します。
![network](https://raw.githubusercontent.com/TechnoTUT/Network/main/network_event.drawio.svg)  
ルーターとしてNEC IX2025、L3スイッチとしてAllied Telesis AT-x600-48Ts、L2スイッチとしてCisco Catalyst 2960+ 24TC-LとAllied Telesis GS924M V2を、無線APにはCisco Aironet 2700を使用しています。  
Pro DJ Link機能により、コンピュータで楽曲情報を取得したり、スマートフォンやタブレットでDJを行ったりすることができます。  
さらに、NDIによって映像をネットワーク経由で送受信したり、仮想基盤を使用したりすることができます。

## ポートについて
ポートとvlanの対応は以下の通りです。  

Allied Telesis AT-x600-48Ts
```
TTUT_CORE_SW#show vlan all
VLAN ID  Name            Type    State   Member ports
                                         (u)-Untagged, (t)-Tagged
======= ================ ======= ======= ====================================
1       default          STATIC  ACTIVE  port1.0.3(u) port1.0.4(u)
                                         port1.0.41(u) port1.0.42(u)
                                         port1.0.43(u) port1.0.44(u)
                                         port1.0.45(u) port1.0.46(u)
                                         port1.0.47(u) port1.0.48(u)
9       ROUTER           STATIC  ACTIVE  port1.0.1(u)
10      DJNW             STATIC  ACTIVE  port1.0.33(u) port1.0.34(u)
                                         port1.0.35(u) port1.0.36(u)
                                         port1.0.41(t) port1.0.42(t)
                                         port1.0.43(t) port1.0.44(t)
                                         port1.0.48(t)
20      VJNW             STATIC  ACTIVE  port1.0.37(u) port1.0.38(u)
                                         port1.0.39(u) port1.0.40(u)
                                         port1.0.41(t) port1.0.42(t)
                                         port1.0.43(t) port1.0.44(t)
                                         port1.0.48(t)
30      LEDNW            STATIC  ACTIVE  port1.0.2(u) port1.0.5(u) port1.0.6(u)
                                         port1.0.7(u) port1.0.8(u) port1.0.9(u)
                                         port1.0.10(u) port1.0.11(u)
                                         port1.0.12(u) port1.0.13(u)
                                         port1.0.14(u) port1.0.15(u)
                                         port1.0.16(u) port1.0.17(u)
                                         port1.0.18(u) port1.0.19(u)
                                         port1.0.20(u) port1.0.21(u)
                                         port1.0.22(u) port1.0.23(u)
                                         port1.0.24(u) port1.0.41(t)
                                         port1.0.42(t) port1.0.43(t)
                                         port1.0.44(t) port1.0.48(t)
40      MGMT             STATIC  ACTIVE  port1.0.25(u) port1.0.26(u)
                                         port1.0.27(u) port1.0.28(u)
                                         port1.0.29(u) port1.0.30(u)
                                         port1.0.31(u) port1.0.32(u)
                                         port1.0.41(t) port1.0.42(t)
                                         port1.0.43(t) port1.0.44(t)
                                         port1.0.48(t)
```

Cisco Catalyst 2960+ 24TC-L
```
TTUT_EDGE_SW1#show vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/4, Fa0/5, Fa0/6, Fa0/7
                                                Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24
10   DJNW                             active    Fa0/1, Fa0/2, Fa0/3
20   VJNW                             active
30   LEDNW                            active
40   MGMT                             active
```

Allied Telesis GS924M V2
```
Manager > show vlan

VLAN Information
--------------------------------------------------
 Name ................ default
 Identifier .......... 1
 Status .............. Static
 Protected Ports ..... None
 Untagged Ports ...... None
 Tagged Ports ........ None
 Spanning Tree ....... default
 Trunk Ports ......... None
 Mirror Port ......... None
 IP Interface ........ None
--------------------------------------------------
 Name ................ DJ
 Identifier .......... 10
 Status .............. Static
 Protected Ports ..... None
 Untagged Ports ...... 9-14
 Tagged Ports ........ 15-16,23-24
 Spanning Tree ....... default
 Trunk Ports ......... None
 IP Interface ........ None
--------------------------------------------------
 Name ................ VJ
 Identifier .......... 20
 Status .............. Static
 Protected Ports ..... None
 Untagged Ports ...... 17-22
 Tagged Ports ........ 15-16,23-24
 Spanning Tree ....... default
 Trunk Ports ......... None
 IP Interface ........ None
--------------------------------------------------
 Name ................ LED
 Identifier .......... 30
 Status .............. Static
 Protected Ports ..... None
 Untagged Ports ...... 1-4
 Tagged Ports ........ 15-16,23-24
 Spanning Tree ....... default
 Trunk Ports ......... None
 IP Interface ........ None
--------------------------------------------------
 Name ................ MGMT
 Identifier .......... 40
 Status .............. Static
 Protected Ports ..... None
 Untagged Ports ...... 5-8
 Tagged Ports ........ 15-16,23-24
 Spanning Tree ....... default
 Trunk Ports ......... None
 IP Interface ........ Yes
--------------------------------------------------
```

NDIを使用する場合は、ギガビットポートを使用してください。
トランクポートはスイッチ同士の接続に用いるか、コンピュータを接続しVLAN IDを指定することで指定したVLANに接続することができます。  

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

## 経路情報の交換について
NEC IX ルータとAllied Telesis AT-x600-48Ts L3スイッチの間では、OSPFによる経路情報の交換を行っています。接続すると自動で経路情報を交換し、通信が可能になります。