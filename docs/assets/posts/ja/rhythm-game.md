# リズムゲーム  
*2022年2月19日*  
<div class="tag-list">
  <span class="tag">TypeScript</span>
  <span class="tag">Angular</span>
  <span class="tag">HTML5 Canvas</span>
  <span class="tag">Webゲーム</span>
  <span class="tag">アーケード</span>
</div>

---

## 概要

**リズムゲーム**は、音楽に合わせてキーを押すことでノーツをタイミングよくヒットさせる、ウェブベースのリズムゲームです。週末プロトタイプとして開発され、クラシックな音ゲーの基本的な仕組みをモダンなウェブ技術で再現しています。

デモでは**League of Legends**のアートと音楽を使用していますが、すべてのアセット（音声、ビジュアル、譜面）はモジュール化されており、簡単に差し替えることができます。

プレイ方法：**再生**ボタンを押し、以下のキーを使って操作します：

<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">A</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">S</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">D</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">F</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:100px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">Space</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">J</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">K</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">L</span>
<span style="display:inline-flex; align-items:center; justify-content:center; width:50px; height:50px; border:2px solid #444; border-radius:6px; margin:4px;">;</span>

---

## 仕組み

- **譜面**は、音楽に合わせたキープレスのタイミングを記録することで生成されます。  
- そのタイムスタンプに基づき、各ノーツがターゲットに到達するタイミングが決まります。  
- ゲームプレイ中は、ユーザーの入力とノーツの位置をリアルタイムで比較します。  
- 判定は**ミス**から**パーフェクト**まで、タイミングの精度によってスコアが決まります。  

---

## 拡張機能とアイデア

基本的なメカニクスは実装済みですが、以下のような拡張も可能です：

- 🧠 ユーザーの曲に対応した**自動譜面生成機能**  
- ⚡ 音楽の波形と同期する**フレーム精度のタイミング処理**  
- 🎨 **コンボエフェクトやノーツアニメーション**などのビジュアル強化  
- 🆚 スコアをリアルタイムで競える**マルチプレイヤーモード**  
- 🎵 ドラッグ＆ドロップやファイルアップロードによる**カスタム曲インポーター**  
- 📈 スコア履歴、難易度、実績などを含む**進行システム**  

---

## デモ  
<a href="./demo/rhythm-game" style="text-decoration: none; color: #007acc; font-weight: bold;">▶️ リズムゲームをプレイ</a>

## ソースコード  
<a href="https://github.com/JLSeto/jimmyset0/tree/master/src/app/beat-music" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 GitHubでソースを見る</a>
