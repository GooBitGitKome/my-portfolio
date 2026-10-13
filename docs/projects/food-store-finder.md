---
title: Food Store Finder — 自前Webサイトなし飲食店検索＆連絡先収集システム
tags:
  - Next.js
  - React
  - TypeScript
  - Python
  - FastAPI
  - uv
  - OpenStreetMap
  - Cloudflare Pages
  - Google Cloud Run
  - ai-driven-development
---

# Food Store Finder

<div align="center">
  <h3>自社公式Webサイト（ホームページ）を保有していない飲食店・食品店を抽出し、営業・支援連絡先を一覧化するフルスタック分析基盤</h3>
</div>

<div class="project-badges" align="center" markdown>
`Next.js 14` `Leaflet` `FastAPI` `Python 3.11+` `uv` `OpenStreetMap (Overpass API)` `Cloudflare Pages` `Google Cloud Run` `AI駆動開発`
</div>

<br>

> **「自社HPを持たない街の魅力的な飲食店をすばやく発掘し、支援や連携へ繋ぐ」**  
> 地図上のピン配置や半径指定、地名入力から、**公式自前Webサイトを持たず大手グルメポータルやSNSのみで営業している飲食店・カフェ・食品店を自動判定**。  
> OSM（OpenStreetMap）と公開Web探索を組み合わせたハイブリッドクローリングにより、E-mailアドレス、電話番号、SNSアカウント、GoogleマップURLを自動収集してExcel対応CSV形式でエクスポートするシステムです。

---

## 🌐 公開デモサイト

ブラウザから直接本システムをお試しいただけます：

[:material-web: **https://food-store-finder.pages.dev/ を開く**](https://food-store-finder.pages.dev/)

- **フロントエンドホスティング**: Cloudflare Pages（グローバルエッジ配信）
- **バックエンド API 実行環境**: Google Cloud Run (`asia-northeast1` 東京リージョン)

---

## 💡 開発背景と解決課題

地域活性化、中小店舗向けWeb制作支援、食材・備品卸売などの営業・連携開拓において、**「自前のホームページをまだ持っていない個人店や地域密着店」にアプローチしたい**という強い需要が存在します。

しかし、従来の手作業や既存ポータル検索には以下の課題がありました：

1. **ポータルサイトと自社サイトの判別の難しさ**:
   - 検索結果に「食べログ」「ぐるなび」「ホットペッパー」「Uber Eats」「Google マップ」などのリンクが表示されても、それが「自前Webサイト」なのか「ポータル掲載」なのかを1件ずつ目視で確認する必要があった。
2. **大手チェーン店の手動除外負荷**:
   - 独自ドメインを持つ大手チェーン店が検索結果の大半を埋め尽くし、支援対象となる地域店を発掘するのに膨大な時間がかかる。
3. **Google Maps API の従量課金コスト**:
   - 地図検索や詳細情報の取得に Places API 等を使うと、リクエスト数に応じて高額な従量課金が発生する。
4. **連絡先の分散**:
   - 電話番号はポータルにあり、メールアドレスは別の公開情報にあり、SNSはInstagramにあるなど、情報が散在してリスト化が困難。

**Food Store Finder** は、OpenStreetMap のオープンデータ基盤とインテリジェントなドメイン判定エンジン、Universal URL スキームを融合させることで、**API課金コストを完全にゼロに抑えながら**、精度の高い店舗リストを瞬時に生成します。

---

## 🌟 主要機能

1. **柔軟な地理空間検索 & 現在地ワンクリック取得**:
   - 地名・住所の自動ジオコーディング（Nominatim 連携）。
   - ブラウザ Geolocation API による現在地からの即時検索。
   - Leaflet マップ上のドラッグ可能なマーカーと探索半径スライダー（100m 〜 最大100km）。
2. **ジャンル分類 & リアルタイムタブ切り替え**:
   - 飲食店・レストラン（🍽️）、カフェ・喫茶（☕）、食品・ベーカリー（🥖）の3大カテゴリを事前選択および取得後ワンクリックフィルタリング。
3. **自社Webサイト有無の精密判定エンジン**:
   - ドメインブラックリスト / ホワイトリスト判定により、食べログ・ぐるなび・ホットペッパー・Uber Eats・出前館・Retty 等のみの店舗を「自社HPなし」と正確に判定。
   - 独自ドメインを保有する店舗や大手チェーン店を自動除外。
4. **連絡先ハイブリッド発掘 (Contact Miner)**:
   - OSMタグと公開Web探索を組み合わせ、メールアドレス、電話番号、住所、公式SNS（Instagram等）を補完。
5. **Google Maps 別ページ誘導 (API課金ゼロ設計)**:
   - Google Maps API キーを使用せず、公式 Universal URL スキームを活用して店舗詳細・外観写真・クチコミページへ直接ジャンプ。
6. **Excel 完全対応の UTF-8 (BOM付き) CSV エクスポート**:
   - 日本語版 Microsoft Excel で開いても文字化けしない UTF-8 BOM 形式でワンクリックダウンロード。

---

## 🏗️ システムアーキテクチャ

```mermaid
flowchart TD
    subgraph Browser["ブラウザ (Next.js 14 on Cloudflare Pages)"]
        MAP["Leaflet 地図 UI\n(ピン配置 / 半径スライダー / 現在地)"]
        TABLE["StoreTable\n(即時フィルタ / 色分けバッジ)"]
        CSV["CSV エクスポート (UTF-8 with BOM)"]
    end

    subgraph CloudRun["FastAPI Backend (Google Cloud Run / uv)"]
        ROUTER["REST API Router (/api/stores/search)"]
        GEO["ジオコーディング (Nominatim)"]
        DISCOVER["店舗探索 (Overpass API / OpenStreetMap)"]
        JUDGE["自前HP判定エンジン (ポータル/SNSドメイン照合)"]
        MINER["連絡先マイナー (メール・SNS発掘)"]
    end

    subgraph External["外部サービス & オープンデータ"]
        NOMINATIM["Nominatim (OSM Geocoding)"]
        OVERPASS["Overpass API (OSM POI データ)"]
        GMAP["Google Maps (Universal URL 遷移)"]
    end

    MAP -->|探索クエリ (lat, lon, radius, genre)| ROUTER
    ROUTER --> GEO
    GEO <--> NOMINATIM
    ROUTER --> DISCOVER
    DISCOVER <--> OVERPASS
    DISCOVER --> JUDGE
    JUDGE --> MINER
    MINER --> ROUTER
    ROUTER --> TABLE
    TABLE --> CSV
    TABLE -->|Universal URL| GMAP
```

---

## 🤖 AI駆動開発 (AI-Driven Development) における実践

本プロジェクトは、新世代の超高速 Python パッケージマネージャー **uv** と AI エージェントの自律協調により、要件定義からデプロイまでを極めてスピーディに完結させました。

### 役割分担（人間の意思決定 vs AIの高速化）
- **自身が担当した領域（ドメイン知見・戦略的判断・アーキテクチャ）:**
  - 「Google Maps API への従量課金をゼロにする」ための Universal URL スキーム活用の意思決定
  - 日本国内の主要グルメポータル・予約サービス（食べログ、ぐるなび、ホットペッパー、Retty 等）のドメイン識別パターンの仕様化
  - 営業・支援の現場で必須となる UTF-8 (BOM付き) CSV 出力フォーマットの要件定義
- **AIが加速した領域（高速実装・テスト自動化・環境構築）:**
  - 複雑な Overpass QL クエリ（`amenity=restaurant`, `shop=bakery` 等の空間結合）の自動最適化
  - `uv` ワークスペース定義（`pyproject.toml`）およびワンストップ起動スクリプト（`start.sh`、`Makefile`）の整備
  - pytest 自動テストスイート（全13件）によるジオコーディング・自前HP判定の境界値テスト網羅
  - アーキテクチャ決定記録（[ADR-0001](file:///app/food-store-finder/docs/adr/ADR-0001-technology-stack.md), [ADR-0002](file:///app/food-store-finder/docs/adr/ADR-0002-osm-hybrid-data-source.md)）の構造化記述

---

## 📊 技術スタック

| 分類 | 技術 / ライブラリ | バージョン / 詳細 |
| :--- | :--- | :--- |
| **フロントエンド** | Next.js, React, TypeScript | Next.js 14 (App Router), Tailwind CSS |
| **地図 UI** | Leaflet, React-Leaflet | オープンソース地図タイル、カスタムマーカー、円形半径描画 |
| **バックエンド** | FastAPI, Python, Uvicorn | Python 3.11+, 非同期ルーティング |
| **パッケージ管理** | uv (Astral) | 超高速仮想環境・ロックファイル管理 (`uv.lock`) |
| **データソース** | OpenStreetMap (Overpass API) | 飲食店・カフェ・食料品店のPOIオープンデータ |
| **インフラ / ホスティング** | Cloudflare Pages, Google Cloud Run | 東京リージョン (`asia-northeast1`), Docker コンテナ |
| **テストフレームワーク** | pytest, pytest-asyncio | 全13件の自動テストによる品質担保 |

---

## 🔗 ディレクトリ & 関連リンク

- **リポジトリ**: [`food-store-finder`](file:///app/food-store-finder)
- **公開デモ**: [https://food-store-finder.pages.dev/](https://food-store-finder.pages.dev/)
- **アーキテクチャ決定記録**:
  - [ADR-0001: 技術スタックの選定](file:///app/food-store-finder/docs/adr/ADR-0001-technology-stack.md)
  - [ADR-0002: OSMとハイブリッドデータソース](file:///app/food-store-finder/docs/adr/ADR-0002-osm-hybrid-data-source.md)
