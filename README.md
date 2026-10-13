# Takeshi Komeda's Tech Portfolio

数理最適化（GA/LHS）のアルゴリズム研究から、自律型AI協調開発による低レイヤ・通信・フルスタックWeb/Mobileプロダクトまでをまとめた技術ポートフォリオサイトです。

Material for MkDocs をベースに構築されており、GitHub Pages にて公開されています。

---

## 🌐 サイト構成 & 掲載コンテンツ

### 1. 🔬 Core Foundations（自力研究・スクラッチ実装）
アルゴリズムの理論的背景の理解に基づき、外部ライブラリに頼らずゼロから設計・実装した数理最適化技術です。

- **[遺伝的アルゴリズム (Genetic Algorithm; GA) 実装 in Python](docs/Optimization/Genetic%20Algorithm%20in%20Python.md)**: 実数値GAの自作実装とベンチマーク検証
- **[Latin Hypercube Sampling (LHS) の理論と有用性](docs/Optimization/Latin%20Hypercube%20Sampling%20(LHS)%20の理論と有用性.md)**: 多次元空間の均一サンプリング手法と設計空間探索

### 2. ⚡ AI-Driven Products（AI協調開発プロダクト）
要件定義・アーキテクチャ設計・実機検証を主導し、自律型AI協調によって高速に具現化したプロダクト群です。

| プロダクト | 概要 | 主な技術スタック |
| :--- | :--- | :--- |
| **[OutdoorCast](docs/projects/outdoor-cast.md)** | 18種アウトドア対応の気象・波浪判定 & PostGIS分析基盤・解説Web | `FastAPI` `React 18` `Capacitor` `Supabase` `Emdash CMS` |
| **[Personal Kakeibo](docs/projects/personal-kakeibo.md)** | 3列ジャンル・日額月額予算の個人用家計簿アプリ & 公式LP | `iOS 17+` `Swift 6` `SwiftData` `CloudKit` `Swift Charts` `Emdash CMS` |
| **[Food Store Finder](docs/projects/food-store-finder.md)** | 自前Webサイトなし飲食店の検索・連絡先収集システム | `Next.js 14` `Leaflet` `FastAPI` `uv` `OpenStreetMap` `Cloudflare Pages` |
| **[思い出の窓 (Memory Window)](docs/projects/memory-window.md)** | 遠隔見守り・生活リズム・Realtime音声対話支援 Web/PWA | `React 18` `TypeScript` `Supabase` `OpenAI WebRTC` `Capacitor` |
| **[MyoLink](docs/projects/myo-link.md)** | 神経筋疾患向けPRO収集・急変アラート判定ヘルスケアアプリ | `Python 3.14` `FastAPI` `React Native` `Expo Web` `Emdash CMS` |
| **[AppAudioRouter](docs/projects/app-audio-router.md)** | macOS 14.2+ Process Tap API を活用した常駐型仮想オーディオルーター | `Swift` `SwiftUI` `CoreAudio` `vDSP` `macOS` `Emdash CMS` |
| **[VirtualKeyboard with iPhone](docs/projects/virtual-keyboard.md)** | iPhoneのタッチ・音声をBLEでPCへ注入する上肢障害者向け入力支援 | `iOS (Swift)` `Python` `bleak (BLE)` `Accessibility` |

---

## 🛠️ ポートフォリオサイトの技術スタック

- **Static Site Generator**: [MkDocs](https://www.mkdocs.org/) (Material for MkDocs)
- **パッケージ・環境管理**: [uv](https://docs.astral.sh/uv/) (Python 3.10+)
- **Plugins / Extensions**:
  - `mkdocs-awesome-pages-plugin` (ディレクトリ階層ベースのナビゲーション制御)
  - `mkdocs-jupyter` (Jupyter Notebook 表示サポート)
  - `mkdocstrings` (Python docstrings 自動ドキュメント生成)
  - `pymdownx.superfences` (Mermaid ダイアグラム描画サポート)
  - `markdown-katex` / `arithmatex` (数式レンダリング)
- **CI / CD**: GitHub Actions (`main` ブランチへのプッシュ時に `uv run mkdocs gh-deploy` で自動デプロイ)

---

## 🚀 ローカル開発手順

### 前提条件
- Python 3.10+
- [uv](https://docs.astral.sh/uv/) がインストールされていること

### 1. 依存関係のインストール
```bash
uv sync
```

### 2. ローカルプレビューサーバーの起動
```bash
uv run mkdocs serve
```
ブラウザで `http://127.0.0.1:8000/` にアクセスして確認できます。ファイルの変更は即時ホットリロードされます。

### 3. 静的サイトのビルド
```bash
uv run mkdocs build
```
`site/` ディレクトリに HTML / CSS / JS / アセット群が生成されます。

---

## 📁 ディレクトリ構成

```text
tech-post-ai/
├── docs/                      # ドキュメントソース (Markdown, Assets)
│   ├── index.md               # ポートフォリオ トップページ
│   ├── .pages                 # ナビゲーション定義 (awesome-pages)
│   ├── projects/              # 各プロダクトの詳細解説ページ & 画像
│   └── Optimization/          # 数理最適化・アルゴリズム解説記事 & Notebook
├── site/                      # ビルド済み静的Webサイト成果物
├── .github/workflows/         # CI/CD パイプライン (GitHub Pages 自動デプロイ)
├── mkdocs.yml                 # MkDocs 設定ファイル
├── pyproject.toml             # プロジェクト設定・依存パッケージ定義
├── uv.lock                    # 依存パッケージロックファイル
└── README.md                  # 本ドキュメント
```

---

## 👤 Author

**Takeshi Komeda (GooBitGitKome)**
- GitHub: [@GooBitGitKome](https://github.com/GooBitGitKome)
