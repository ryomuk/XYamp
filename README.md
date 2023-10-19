# XYamp
Deflection amplifier to mod a CRT into an XY monitor. Mainly designed for the SONY watchman and the SCOPETREX.

This document is written mostly in Japanese. If necessary, please use a translation service such as DeepL (I recommend this) or Google.

# 概要
白黒CRTをXYモニターとして使うための回路です．SCOPETREX( https://github.com/schlae/scopetrex )の出力をSONY watchmanに表示させるために作りました．

watchman FD-10
![](images/FD10_vectrextitle.jpg)

watchman FD-40
![](images/FD40_vectrextitle.jpg)

主な構成要素は下記の3種類の回路です．
- X, Y信号で偏向コイルを駆動するためのアンプ
- Z信号(輝度信号)でG1グリッドを駆動するためのアンプ
    - WatchmanのCRTはカソードではなくG1で輝度を調整しています．
- フライバックトランス(高電圧生成)用の16kHzの信号発振器

# 動画
動作している様子です．

[![](https://img.youtube.com/vi/gAd8rqS27hQ/0.jpg)](https://www.youtube.com/watch?v=gAd8rqS27hQ)

# 回路の説明
## XY軸(偏向)用アンプ
![](images/sch_xy.png)

## Z軸(輝度)用アンプ
![](images/sch_z.png)

## フライバック信号発振器
![](images/sch_flyback.png)

## BOM

| |Reference|Qty|Value|Memo|
|---|---|---|---|---|
|1|C1|1|0.01u||
|2|C2, C4, C6, C7|4|1u||
|3|C3|1|4700p||
|4|C5|1|2.2u||
|5|C8, C9, C12, C13|4|47u||
|6|C10, C11, C14, C15|4|0.1u||
|7|D1|1|1N4148||
|8|J1|1|X||
|9|J2|1|Xout||
|10|J3|1|Flyback Signal||
|11|J4|1|Y||
|12|J5|1|Yout||
|13|J6|1|Z||
|14|J7|1|Zout||
|15|J8|1|Conn_01x03||
|16|PS1|1|MAU109||
|17|R1|1|3.3k||
|18|R2, R4, R11, R13, R14, R16, R18, RV11|8|1k||
|19|R3, R8, R12, R19|4|10||
|20|R5, R6, R9, R10, R15, RV1, RV4, RV7, RV10, RV13|10|10k||
|21|R7, R17|2|4.7||
|22|RV2, RV8|2|3k||
|23|RV3, RV9|2|1M||
|24|RV5|1|5k||
|25|RV6, RV12|2|100k||
|26|U1, U3|2|AD8397||
|27|U2|1|NE555P||
|28|U4|1|TL072||

# 接続方法
## watchman FD-10
![](images/FD10_pcb.jpg)

## watchman FD-40
![](images/FD40_yoke.jpg)
![](images/FD40_G1.jpg)
![](images/FD40_sch.jpg)
![](images/R509.jpg)
![](images/R801.jpg)

# 調整方法
調整箇所は下記の通り．
## アンプ側
- X, Yの入力振幅とオフセット
- X, Yの偏向コイルの補償
- X, Yの帰還信号(経路1)
- X, Yの帰還信号(経路2)
- Zの入力振幅とオフセット
- Zの倍率
- フライバック信号の周波数
    - 16kHzぐらいにする
## watchman側
- 輝度
- フォーカス

# ブレッドボード版プロトタイプ
![](images/breadboard.jpg)
- とりあえずブレッドボードに組んで動作しました．
- ブレッドボードなのが原因かは不明ですが信号が若干揺れます．

## 画像
![](images/FD10_starhawk.jpg)
![](images/FD10_test.jpg)
![](images/FD40_testd1.jpg)
![](images/FD40_testd2.jpg)
![](images/FD40_testi.jpg)

# ToDo
- 基板作成
- 電源はバッテリーにしたい．
- vectrex部分もwatchmanの筐体に内蔵したい．
    - https://github.com/ryomuk/tangnano20k-vectrex みたいなやつ?

# 参考にした文献，サイト等
## watchman関連
- https://github.com/lucysrausch/sony-scopeman
- https://vintage-technics.ru/Eng-Sony_FD-40A.htm
    - FD-40Aの回路図あり．
    - 検索したらFD-10やFD-20の回路図もネット上にあるみたい．

## 偏向コイルの補償について
- https://www.youtube.com/watch?v=PtxpeOIiFUw

## Vectrex, Scopetrex関連
- https://github.com/schlae/scopetrex
- https://www.e-basteln.de/arcade/asteroids/monitor/

## XYモニター関連
- https://www.jmargolin.com/xy/xymon.htm

## オペアンプの並列接続について
「オペアンプ 大容量」でググって出てきたのがこちら．
- https://www.digikey.jp/ja/articles/control-amplify-high-voltages-effectively-high-voltage-op-amp
    - 元のデータシートはこちら https://www.ti.com/product/ja-jp/OPA454    

# 更新履歴
- 2023/10/18: 初版公開


