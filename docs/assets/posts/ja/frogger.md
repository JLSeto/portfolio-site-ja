# フロッガー 🐸

*2021年8月8日*

<div class="tag-list">
  <span class="tag">TypeScript</span>
  <span class="tag">Angular</span>
  <span class="tag">HTML5 Canvas</span>
  <span class="tag">Webゲーム</span>
  <span class="tag">アーケード</span>
</div>

---

## 概要

このプロジェクトは、クラシックなアーケードゲーム「フロッガー」を**TypeScript**でリメイクし、**Angular**プロジェクトに統合したものです。構造の明確化と型安全性の向上を目指しています。

目的はシンプル：**バグに当たらずに鍵までたどり着くこと**。  
成功するたびに、敵が増えた状態で再スタートします。  
敵にぶつかると、スタート地点に戻されます。

---

## 技術スタック

- **HTML** — キャンバス構造とレイアウト  
- **CSS** — スプライトとビジュアルスタイル  
- **JavaScript** — 元のゲームロジックとループエンジン  
- **TypeScript** — 型安全なロジックへのリファクタリングとAngular統合  

---

## 仕組み

このゲームは3つの主要なレイヤーで構成されています：

### 🎮 エンジン
- ゲームループの制御  
- キャンバスの描画とフレーム更新を処理  

### 🧰 リソース
- 画像アセットのプリロードとキャッシュ管理  
- 全スプライトの読み込み完了を保証  

### 🧍 アプリケーションレイヤー
- プレイヤー、敵、鍵などのコアエンティティを定義  
- 状態、移動、当たり判定の管理  
- キーボード入力の監視  

---

## デモ  
<a href="./demo/frogger" style="text-decoration: none; color: #007acc; font-weight: bold;">▶️ フロッガーをプレイ</a>

## ソースコード  
<a href="https://github.com/JLSeto/jimmyset0/tree/master/src/app/frogger" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 GitHubでソースを見る</a>
