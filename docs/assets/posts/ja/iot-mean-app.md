# Arduino 101 と MEAN スタックを用いたリアルタイム IoT データ可視化

*2021年8月8日*

<div class="tag-list">
  <span class="tag">IoT</span>
  <span class="tag">BLE</span>
  <span class="tag">Arduino101</span>
  <span class="tag">Intel Edison</span>
  <span class="tag">MEANスタック</span>
  <span class="tag">Nodejs</span>
  <span class="tag">WebSockets</span>
  <span class="tag">センサーデータ</span>
  <span class="tag">リアルタイム可視化</span>
</div>

<p align="left">
  <img src="/assets/projects/iot-mean-app/arduino101.jpg" alt="arduino101" style="max-width: 500px; width: 100%; height: auto; border-radius: 5px;" />
  <em style="display: block; margin-top: 6px; color: #666; font-size: 0.9rem;">図：自作の Arduino 101 の写真</em>
</p>

---

## 概要

このプロジェクトでは、**Intel Curie モジュール**を搭載した **Arduino 101** を使用し、**MEANスタック**（MongoDB, Express, AngularJS, Node.js）と連携したリアルタイム IoT システムを構築しています。Arduino 101 は加速度およびジャイロスコープのデータを収集し、**BLE（Bluetooth Low Energy** を通じてブロードキャストします。

クライアント端末は BLE 経由で Arduino 101 に接続し、データを取得して Wi-Fi 経由で Node.js サーバーへ転送します。サーバーは受信したデータを **MongoDB** に保存しつつ、同時にウェブフロントエンドにプッシュしてリアルタイムで可視化を行います。また、ウェブページからは Arduino 101 の**サンプリング周波数**をリモートで変更可能で、その変更は BLE の遅延・Wi-Fi 転送・Arduino の処理時間を加味して、即座にデータフローとグラフに反映されます。

以下はシステム構成図です：

<p align="center">
  <img src="/assets/projects/iot-mean-app/arduino101_diagram_db.png" alt="システム構成図" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## 仕組み

### Arduino 101

Arduino 101 のファームウェアは、`CurieBLE` と `CurieIMU` ライブラリを使った標準的な Arduino コードで記述されています。このボードは BLE ペリフェラルとして機能し、**7つのキャラクタリスティック**を持つ 1つのサービスを公開します：

- **読み取り専用（6つ）**：加速度 (`ax`, `ay`, `az`) および ジャイロスコープ (`gx`, `gy`, `gz`)  
- **書き込み可能（1つ）**：サンプリング周波数 (`ts`)  

各キャラクタリスティックには **UUID** が割り当てられており、クライアントは購読、読み取り、書き込み、通知の受信が可能です。

---

### クライアント端末

クライアント側の Node.js スクリプトは **Noble** ライブラリを使って BLE 経由で Arduino 101 を検出・接続します。接続後、7つのキャラクタリスティックすべてに対して通知を有効にし、サービスを購読します。

**Socket.io** を使って、センサーデータとサンプリング周波数の変更をリアルタイムで Node.js サーバーへ送信します。

> **なぜ WebSockets ではなく Socket.io を使用？**  
> Socket.io はマルチプレクシング（複数のイベントストリームを1つの接続で処理）をシンプルに実装できるため選ばれました。WebSocket よりもオーバーヘッドが少なく、API も扱いやすいです。

---

### サーバー & Webインターフェース

**Node.js** と **Express** で構築されたサーバーは、Socket.io を通じてクライアントからセンサーデータを受け取り、**MongoDB** に保存します。同時に、Socket.io を使ってデータをウェブフロントエンドにブロードキャストします。

フロントエンドは **AngularJS** で構築され、**Bootstrap** によりスタイリングされています。センサーデータは **Google Charts** を用いてリアルタイムグラフで表示され、ユーザーはインターフェースから Arduino 101 のサンプリング周波数を変更できます。この変更は即座にシステム全体へ反映され、リアルタイムデータとして視覚化されます。

---

## デモ & ソースコード

<a href="https://github.com/JLSeto/Arduino101" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 GitHubでソースを見る</a>

<div style="display: flex; flex-direction: column; align-items: center; width: 100%; max-width: 800px; margin: 0 auto;">
  <div style="position: relative; width: 100%; padding-bottom: 56.25%; overflow: hidden; border-radius: 12.5px; box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);">
    <iframe
      src="https://www.youtube.com/embed/x961tXPIoRY"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 12.5px; border: 0; display: block;">
    </iframe>
  </div>
</div>

---
