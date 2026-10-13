---
hide:
  - navigation
  - toc
---

# Takeshi

## AI & IT Engineer / Board Member

**数理最適化（GA/LHS）の数理基盤**と10年以上のNPO理事経験を軸に、**自律型AI協調開発（AI-Driven）**によって低レイヤ・通信・フルスタックアプリを迅速に具現化するエンジニアです。

[:material-github: GitHub Profile](https://github.com/GooBitGitKome){ .md-button .md-button--primary }
[:material-folder-multiple: すべてのプロジェクトを見る](./projects/index.md){ .md-button }

---

## 🌟 Featured Projects

<div class="grid cards" markdown>

-   **OutdoorCast (18種気象判定 & Emdash Web)**

    ![OutdoorCast Hero](./projects/assets/outdoor-cast/hero-visual.svg){ width="48" style="float: right;" }

    [:material-arrow-right-circle: 詳細を見る](./projects/outdoor-cast.md)

    全18種のアウトドアに対応した気象・波浪・地理空間（PostGIS）分析基盤と、Emdash CMS による18種目マトリクス・シミュレーター解説Web。

    `FastAPI` `React 18` `Capacitor` `Supabase` `Emdash CMS` `AI駆動開発`

-   **Personal Kakeibo（個人用家計簿）**

    ![Personal Kakeibo Icon](./projects/assets/personal-kakeibo/app-icon.png){ width="44" style="float: right; border-radius: 8px;" }

    [:material-arrow-right-circle: 詳細を見る](./projects/personal-kakeibo.md)

    iOS・iPadOS 17+ 向け個人用家計簿。3列ジャンル、日額・月額予算、SwiftData ＆ CloudKit Private Database 同期。Emdash CMS 公式Web。

    `iOS 17+` `Swift 6` `SwiftData` `Swift Charts` `CloudKit` `Emdash CMS` `AI駆動開発`

-   **Food Store Finder**

    [:material-arrow-right-circle: 詳細を見る](./projects/food-store-finder.md)

    自前Webサイトなし飲食店検索＆連絡先収集システム。API課金ゼロの Google Maps Universal URL と OSM Overpass API 連携。

    `Next.js 14` `Leaflet` `FastAPI` `uv` `OpenStreetMap` `Cloudflare Pages` `Cloud Run` `AI駆動開発`

-   **思い出の窓 (Memory Window)**

    ![Memory Window Preview](./projects/assets/memory-window/weather-window-preview.png){ width="52" style="float: right; border-radius: 6px;" }

    [:material-arrow-right-circle: 詳細を見る](./projects/memory-window.md)

    白黒線画の窓の向こうに描く、遠隔見守り・生活リズム・対話支援 Web/PWA。OpenAI Realtime WebRTC 音声対話と版付き同意の支援者共有。

    `React 18` `TypeScript` `PWA` `packages/core` `Supabase` `WebRTC` `Capacitor` `AI駆動開発`

-   **MyoLink（マイオリンク）**

    [:material-arrow-right-circle: 詳細を見る](./projects/myo-link.md)

    神経筋疾患患者向けの医療PRO収集と急変アラート判定を行うヘルスケアアプリ。Emdash CMS による広報展開も進行中。

    `Python 3.14` `FastAPI` `React Native` `Expo Web` `Emdash CMS` `AI駆動開発`

-   **AppAudioRouter**

    ![AppAudioRouter Icon](./projects/assets/app-audio-router/AppIcon.png){ width="44" style="float: right; border-radius: 8px;" }

    [:material-arrow-right-circle: 詳細を見る](./projects/app-audio-router.md)

    macOS 14.2+ Process Tap API を活用した、常駐型仮想オーディオルーター。Emdash CMS による公式プロダクトLP。

    `Swift` `SwiftUI` `CoreAudio` `vDSP` `macOS` `Emdash CMS` `AI駆動開発`

-   **VirtualKeyboard with iPhone**

    ![VirtualKeyboard Icon](./projects/assets/virtual-keyboard/virtualkeyboard-icon.svg){ width="44" style="float: right;" }

    [:material-arrow-right-circle: 詳細を見る](./projects/virtual-keyboard.md)

    iPhoneのタッチ・音声をBLE経由でPCへ注入する、上肢障害者向け入力支援システム。Emdash によるアクセシビリティ訴求LP。

    `iOS (Swift)` `Python` `BLE` `Accessibility` `Emdash` `AI駆動開発`

-   **遺伝的アルゴリズム (GA) 実装 in Python**

    [:material-arrow-right-circle: 詳細を見る](./Optimization/Genetic%20Algorithm%20in%20Python.md)

    実数値遺伝的アルゴリズム（Real-coded GA）のスクラッチ実装と最適化解説。

    `Python` `NumPy` `Optimization` `自力実装`

</div>

---

## 🛠️ Core Domains & Tech Stack

### 🔬 Core Foundations（自力研究・スクラッチ実装）
数理理論の深い理解に基づき、アルゴリズムをゼロから自力設計・実装した中核基盤です。

- **数理最適化 & 科学計算:** 遺伝的アルゴリズム (GA), ラテン超格子サンプリング (LHS), CFDサロゲートモデル
- **主要技術:** Python, NumPy, SciPy, Scikit-learn, C / C++
- **ドメイン知見:** 10年以上のNPO理事経験、アクセシビリティ評価設計

---

### ⚡ AI-Driven Products（AI協調開発・高速具現化）
要件定義・アーキテクチャ設計・実機検証を主導し、自律型AI協調により迅速に具現化したプロダクト群です。

- **広報・宣伝 Web エコシステム (`*-web`):**  
  `Emdash CMS` `Astro SSR` `SQLite (data.db)` `Phosphor Icons` `CSS Tokens`
- **音声 & 低レイヤ (AppAudioRouter):**  
  `Swift 5.9+` `SwiftUI` `CoreAudio (Process Tap)` `vDSP` `macOS`
- **アクセシビリティ & 通信 (VirtualKeyboard):**  
  `iOS (Swift)` `CoreBluetooth` `Python` `bleak (asyncio)`
- **フルスタック Web & Mobile (OutdoorCast / Personal Kakeibo / Memory Window / Food Store Finder / MyoLink):**  
  `Swift 6 (SwiftData / CloudKit)` `React 18 / Next.js 14` `TypeScript` `FastAPI` `Supabase (PostGIS / Edge Functions)` `WebRTC` `Capacitor`
- **開発運用 & テスト:**  
  `uv` `pytest` `Playwright` `Deno Test` `Golden Tests`

---

## 👤 Information & Experience

- **Social Leadership (2012 — Present)**: 非営利団体の理事として14年間にわたり従事。組織マネジメント、国際交流、福祉支援技術の開発を担当。
- **Academic Background**: 会津大学 (University of Aizu) コンピュータ理工学部 卒業
- **Languages**: 日本語 (Native) / English (TOEIC 780)
- **Contact / GitHub**: [github.com/GooBitGitKome](https://github.com/GooBitGitKome)

---