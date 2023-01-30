# amx-a (アダプト地図XMLベクトルタイルa) 仕様

## amx-a の目的
- 法務省がG空間情報センターを通じて公開する地図XMLをウェブ地図上でスマートに表示する方法を実証すること。

## amx-a の性格
- [PMTiles](https://github.com/protomaps/PMTiles) 形式で配布
- オープンソースソフトウェアで構築

## デモサイト
- https://amx-project.github.io/a
- https://protomaps.github.io/PMTiles/?url=https%3A%2F%2Fx.optgeo.org%2Fa.pmtiles

## データ配布
- `https://x.optgeo.org/a.pmtiles`
- `https://habs.rad.naro.go.jp/spatial_data/amx/a.pmtiles`

ミラーいただき感謝します。

## ベクトルタイル設計情報
### daihyo
地図XMLデータがある位置を小縮尺でも把握できるようにするための代表点レイヤです。Tippecanoe の機能により間引きます。
#### ズームレベル範囲
2-13

#### 属性
属性は全て外してあります。

#### 生産用スクリプト
https://github.com/amx-project/a/blob/main/daihyo.rb

### fude
地図XMLデータそのものを可能な限り生かしたレイヤです。Tippecanoe によるデータの間引きを行っていません。
#### ズームレベル範囲
14-16

#### 属性
属性のうち、`筆ID`、`version`、`代表点緯度`、`代表点経度`以外はそのまま生かしています。結果として、次の属性がついていると認識しています。

- 座標系 e.g. 公共座標1系
- 測地系判別　e.g. 変換
- 地図名
- 地図番号
- 縮尺分母 e.g. 1000
- 市区町村コード e.g. 42212
- 市区町村名 e.g. 西海市
- 大字コード e.g. 025
- 丁目コード e.g. 000
- 小字コード e.g. 0000
- 予備コード e.g. 00
- 大字名 e.g. 西海町太田原郷
- 地番
- 精度区分 e.g. 乙一
- 座標値種別 e.g 図上測量

`筆ID`、`version`、`代表点緯度`、`代表点経度` を外す処理は、Tippecanoe のコマンドラインオプション `-x` により、　https://github.com/amx-project/a/blob/main/Rakefile で行っています。

#### 生産用スクリプト
https://github.com/amx-project/a/blob/main/fude.rb

## データ生産用スクリプト
- https://github.com/amx-project/a
ここに、バグも含めて全て書いてあります。

## ChangeLog
- 2023-01-31: 作成
