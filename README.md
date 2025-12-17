# Complex Analysis & Wave Packet Integrated Lab
(複素関数論・統合学習ラボ)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-blue.svg)](https://[YOUR_USERNAME].github.io/[REPO_NAME]/)
## 📖 概要 (Overview)

[**🚀 Live Demo**](https://funmatu.github.io/complex-wave-lab/)

**Complex Analysis & Wave Packet Integrated Lab** は、Webブラウザ上で動作する対話型の数学・物理シミュレーション環境です。Three.js (WebGL) を活用し、抽象的な数学概念や物理現象を3次元空間上で直感的に理解することを目的としています。

本プロジェクトは、以下の2つの主要なモジュールを統合しています：

1.  **物理シミュレーション (Wave Packet Simulation):**
    * 量子力学や波動工学における「群速度」と「位相速度」の違いを可視化する波束シミュレーター。
2.  **数学ギャラリー (Complex Functions Gallery):**
    * 複素関数 $f(z)$ の振る舞い（絶対値と偏角）を3D地形図として可視化するリーマン面ビジュアライザー。

特別な環境構築を必要とせず、単一のHTMLファイルのみで動作する軽量設計でありながら、MathJaxによる数式表示と滑らかな3D描画を実現しています。

---

## 🚀 機能詳細 (Features)

### 1. 物理シミュレーション: 位相速度 vs 群速度
波動における「搬送波（Carrier）」と「包絡線（Envelope）」の運動の分離をシミュレートします。

* **数理モデル (1次元ガウス波束):**  
  $$\psi(x,t) = \underbrace{e^{-\frac{(x - v_g t)^2}{2\sigma^2}}}{\text{Envelope}} \cdot \underbrace{e^{i k (x - v_p t)}}{\text{Carrier}}$$
* **可視化要素:**
    * **螺旋（Cyan）:** 複素波動関数 $\psi(x,t)$ の実部・虚部を空間上の螺旋として描画。
    * **射影（Green/Pink）:** 実平面（Real）および虚平面（Imaginary）への射影。
    * **包絡線（White Dashed）:** 波の振幅の概形。
    * **マーカー:** 群速度（ $v_g$ ）で動く赤点と、位相速度（ $v_p$ ）で動く緑点を表示し、両者の速度差を視覚的に追跡可能。
* **調整可能なパラメータ:**
    * **波数 ($k$):** 波の細かさ。
    * **位相速度 ( $v_p$ ):** 搬送波（中身の波）が進む速度。
    * **群速度 ( $v_g$ ):** 包絡線（波の塊）が進む速度。
    * **分散 ($\sigma$):** 波束の広がり具合。

### 2. 数学ギャラリー: 複素関数の3D可視化
複素平面上の関数 $w = f(z)$ を、以下のルールに従って3次元プロットします。

* **座標定義:**
    * $x$ 軸: 実部 $\text{Re}(z)$
    * $y$ 軸: 絶対値 $|f(z)|$ （高さとして表現）
    * $z$ 軸: 虚部 $\text{Im}(z)$
* **色彩表現 (Domain Coloring):**
    * 偏角 $\arg(f(z))$ を色相（HSV）にマッピング。
    * $0 \to 2\pi$ の変化が `赤 -> 黄 -> 緑 -> 青 -> 赤` に対応。
* **実装されている関数:**
    * $f(z) = z^2$: 2価関数、放物面的な広がり。
    * $f(z) = z^3 - 1$: 1の3乗根の配置。
    * $f(z) = 1/z$: 原点における極（Pole）と発散。
    * $f(z) = e^z$: 指数関数的増大と周期性。
    * $f(z) = \sin z$: 鞍部（Saddle point）構造。
    * $f(z) = \sqrt{z}$: 分岐切断（Branch Cut）とリーマン面構造。
    * $f(z) = \log z$: 対数螺旋と分岐。

---

## 🛠 技術スタック (Tech Stack)

本プロジェクトは外部ビルドツール（Webpack/Vite等）を意図的に排除し、学習と移植性を優先した「Single File Component」構成を採用しています。

* **Core:** HTML5, CSS3, Vanilla JavaScript (ES6+)
* **Rendering Engine:** [Three.js (r128)](https://threejs.org/) - CDN経由で読み込み
* **Camera Control:** OrbitControls - 直感的な視点操作
* **Math Rendering:** [MathJax](https://www.mathjax.org/) - LaTeX形式の数式描画

### 依存ライブラリ (CDN)
```html
<script src="[https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js)"></script>
<script src="[https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js](https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js)"></script>
<script src="[https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js](https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js)"></script>

```

---

## 📦 インストールと使用方法 (Installation & Usage)

### ローカルでの実行

本アプリケーションはサーバーサイドの処理を一切必要としません。

1. リポジトリをクローン、またはZIPとしてダウンロードします。
```bash
git clone https://github.com/Funmatu/complex-wave-lab.git

```


2. `index.html` を任意のモダンブラウザ（Chrome, Firefox, Edge, Safari）で開きます。
* ※ダブルクリックで直接開くだけで動作します。



### 操作マニュアル

画面右側のUIパネルで操作を行います。

1. **タブ切り替え:** 上部のタブで「① 物理シミュ」と「② 数学ギャラリー」を切り替えます。
2. **物理シミュモード:**
* `再生 / 停止` ボタンで時間の進行を制御します。
* スライダーで k, v_p, v_g, \sigma をリアルタイムに変更可能です。
* **ヒント:** v_p = 2.0, v_g = 1.0 のように設定すると、波が後ろから現れて前方に消えていく（物質波の典型的な）挙動が観察できます。


3. **数学ギャラリーモード:**
* ドロップダウンメニューから可視化したい関数を選択します。
* 数式と簡単な解説が表示され、3Dモデルが即座に更新されます。


4. **視点操作:**
* **回転:** 左クリックドラッグ
* **ズーム:** ホイールスクロール
* **パン（平行移動）:** 右クリックドラッグ



---

## 📐 数学的・物理学的背景 (Theoretical Background)

### 波束 (Wave Packet) の一般論

量子力学において粒子は波動関数 \psi(x,t) で記述されます。自由粒子の波動関数は平面波の重ね合わせ（波束）として表現され、その重心の速度（群速度 v_g）は古典的な粒子の速度 v = p/m に対応します。一方、波の位相が進む速度（位相速度 v_p）は v_p = E/p となり、非相対論的自由粒子では v_p = v_g / 2 となることが知られています。本シミュレーターはこの現象を視覚的に検証するために設計されています。

### 複素関数の可視化 (Complex Function Plotting)

複素関数 w = f(z) は4次元的な情報（入力2次元、出力2次元）を持つため、通常の3次元グラフでは表現しきれません。本ツールでは「絶対値を高さ」「偏角を色」に割り当てる手法を採用しています。

* **極 (Pole):** |f(z)| \to \infty となる点は、グラフ上で無限に高い山として表現されます（例: 1/z）。
* **分岐切断 (Branch Cut):** 多価関数（\sqrt{z}, \log z）を一価にするために定義域を切断した境界線は、色の不連続な「段差」として視覚化されます。

---

## 📂 ディレクトリ構成 (File Structure)

```text
.
├── index.html       # アプリケーションの全ソースコード（HTML/CSS/JS）
├── README.md        # 本ドキュメント
└── LICENSE          # ライセンスファイル

```

※ 本プロジェクトは意図的に単一ファイル (`index.html`) にロジックを集約しています。これにより、USBメモリでの配布や、インターネット接続のない環境での教育利用を容易にしています。

---

## 🔮 今後のロードマップ (Roadmap)

* **波動シミュレーション:**
* ポテンシャル障壁によるトンネル効果のシミュレーション追加。
* 2次元波束への拡張。


* **複素関数:**
* ユーザー定義関数の入力パーサー実装。
* リーマン球面上への射影モードの追加。


* **システム:**
* WebXR対応（VRヘッドセットでの没入型観察）。



---

## 📜 ライセンス (License)

本ソフトウェアは **MIT License** の下で公開されています。
詳細は [LICENSE](https://www.google.com/search?q=./LICENSE) ファイルをご確認ください。

Copyright (c) 2025 Funmatu
