# 日本の測地系アプリ — JP-GeoConverter Pro / JP-GeoPrism / GeoDiveExa

日本の測地系（東京測地系・JGD2000・JGD2011・JGD2024）と平面直角座標系を、現場と学習の両方で扱うための iOS アプリ群のドキュメントです。コードは公開していません。ここには「何ができるか・どの座標系と補正に対応しているか・精度をどう確かめているか」をまとめ、詳しい解説は各公式サイトの記事へつなぎます。

[English](README.en.md)

---

## アプリ一覧

| アプリ | 内容 | App Store | 公式サイト |
| --- | --- | --- | --- |
| **JP-GeoConverter Pro**（旧 GeoConverter Pro） | 座標変換専用アプリ。世界測地系／東京測地系／平面直角座標系の相互変換に加え、セミダイナミック補正・定常時地殻変動補正・ジオイド 2011／2024 による標高の扱いに対応。手入力と CSV 一括変換ができ、全機能がオフラインで動きます | [App Store](https://apps.apple.com/app/id6761740960) | [gcpro.y42u.net](https://gcpro.y42u.net/) |
| **JP-GeoPrism** | 測地系のズレやジオイドを地図・ヒートマップで可視化して学ぶアプリ。クイズ機能つき | [App Store](https://apps.apple.com/app/id6780149823) | [gmp.y42u.net](https://gmp.y42u.net/) |
| **GeoDiveExa** | RTK-GNSS 対応の高精度位置調査アプリ。座標変換エンジンの原点 | — | [y42u.net/tec001](https://y42u.net/tec001/) |

> App Store 上の表示名は、名称変更（2026 年 11 月）を含む次のアップデートの公開時に切り替わります。App Store の ID・リンク先は変わりません。

---

## このドキュメントの目次

| ページ | 内容 |
| --- | --- |
| [geoconverter-pro/README.md](geoconverter-pro/README.md) | JP-GeoConverter Pro の概要・対応座標系・補正の要点・FAQ 10 問・関連記事 |
| [geoconverter-pro/supported-systems.md](geoconverter-pro/supported-systems.md) | 対応する測地系・座標系・補正・内蔵パラメータの一覧表 |
| [glossary.md](glossary.md) | 測地系・座標系の用語集（30 語） |
| geoprism-jp/ | JP-GeoPrism の概要・できる可視化の一覧・FAQ（準備中） |
| geodiveexa/ | GeoDiveExa の概要・RTK-GNSS 対応の要点（準備中） |
| geocore/ | 共有エンジン GeoCoreJP の説明（準備中） |

---

## 共有エンジン GeoCoreJP

JP-GeoConverter Pro と JP-GeoPrism は、GeoDiveExa から抽出した座標変換エンジン **GeoCoreJP**（Swift Package）を共有しています。GeoCoreJP が計算するのは、東京測地系と JGD2000 の相互変換（TKY2JGD）、2003 年以降の地震に伴う座標補正（jgdMerge2011／2024）、セミダイナミック補正（SemiDyna）、定常時地殻変動補正（pos2jgd）、平面直角座標系 第 1〜19 系と緯度経度の相互変換、そしてジオイドモデル 2011／2024 による楕円体高と標高の換算です。国土地理院が公開するパラメータファイルを内蔵し、すべての計算をデバイス内で完結させます。精度は、国土地理院の公式ツール（TKY2JGD・PatchJGD・SemiDynaEXE・POS2JGD）との全数比較で確かめています（[検証記事](https://gcpro.y42u.net/2026/06/17/gsi-coordinate-validation/)）。

- [高精度を支える GeoCoreJP の設計思想](https://gcpro.y42u.net/2026/06/03/geocore-precision-design/)
- [PROJ で足りること・足りないこと — 日本特化エンジン GeoCoreJP を作った理由](https://gcpro.y42u.net/2026/07/09/proj-geocore-comparison/)

---

## 本で学ぶ

座標がズレる理由から実務での扱いまでを通しで読むなら、Kindle 本『日本の測地系がわかる本』シリーズ 3 冊（[本編](https://www.amazon.co.jp/dp/B0H971W8WX)・[実装編](https://www.amazon.co.jp/dp/B0H97LPNH3)・[Q&A](https://www.amazon.co.jp/dp/B0HF4SJC1L)）があります（Kindle Unlimited 対象）。

---

## 開発者

アプリ・Kindle 本・公開プロジェクトの一覧は [GitHub: amru195704](https://github.com/amru195704) にまとめています。
