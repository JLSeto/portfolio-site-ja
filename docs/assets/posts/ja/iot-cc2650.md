# CC2650 SensorTag を使った IoT データ可視化

*2017年12月5日*

<div class="tag-list">
  <span class="tag">#IoT</span>
  <span class="tag">#Texas Instruments CC2650</span>
  <span class="tag">#Nodejs</span>
  <span class="tag">#センサーデータ</span>
</div>

<p align="left">
  <img src="/assets/projects/cc2650/cc2650.jpg" alt="CC2650 sensor" style="max-width: 500px; width: 100%; height: auto; border-radius: 5px;" />
  <em style="display: block; margin-top: 6px; color: #666; font-size: 0.9rem;">図：自作の CC2650 センサーの写真</em>
</p>

---

## 概要

Texas Instruments の **CC2650 SensorTag** は、加速度や温度などの実世界データを取得できるコンパクトなセンサープラットフォームで、IoT アプリケーションの迅速なプロトタイピングに最適です。SensorTag は **TI SensorTag アプリ** を使って Bluetooth 経由でスマートフォンに簡単に接続できます。このアプリではリアルタイムでセンサーの値を確認できるほか、ボタンひとつでデータを **IBM の QuickStart プラットフォーム** に Wi-Fi 経由で送信することも可能です。

IBM のプラットフォームにはデータ分析や IoT アプリのホスティングに便利な機能がありますが、本プロジェクトでは異なるアプローチを採用しています。IBM のダッシュボードを使う代わりに、**Node-RED** と **WebSocket** を用いて IBM クラウドからデータを取得し、独自に構築したウェブインターフェースへ送信します。以下の図はシステム全体の構成を示しており、このデモのために構築した部分をハイライトしています：

<p align="center">
  <img src="/assets/projects/cc2650/cc2650_diagram.png" alt="システム構成図" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## 仕組み

バックエンドサーバーは **Node.js** を使って構築されており、視覚的にデータフローを構築できるツールである **Node-RED** を統合しています。これにより、ロジックをフローチャートのように接続して扱うことが可能になります。

IBM クラウドからデータを取得するには、Node-RED の `ibmiotapp` モジュールを使用します。このモジュールが SensorTag のデータストリームを購読し、受信したデータを Node-RED の **WebSocket** ノード経由で Node.js サーバーへ転送します。

サーバー側では **WebSocket** を使ってフロントエンドのウェブページにデータを送信し、**HTML**、**CSS**、**JavaScript** を使って生データを表示します。さらに、**Google Charts** を統合することで、SensorTag の x, y, z 軸の加速度データをリアルタイムでグラフ表示しています。

<p align="center">
  <img src="/assets/projects/cc2650/middleware.png" alt="システム構成図" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## デモ & ソースコード

<a href="https://github.com/JLSeto/CC2650" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 GitHubでソースを見る</a>

<div style="display: flex; flex-direction: column; align-items: center; width: 100%; max-width: 800px; margin: 0 auto;">
  <div style="position: relative; width: 100%; padding-bottom: 56.25%; overflow: hidden; border-radius: 12.5px; box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);">
    <iframe
      src="https://www.youtube.com/embed/2XyzMGU4GSo"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 12.5px; border: 0; display: block;">
    </iframe>
  </div>
</div>

---
