# pico-w-blinky
raspberry pi pico w の オンボードLEDでLチカをする[プロジェクト](https://github.com/embassy-rs/embassy/blob/main/examples/rp/src/bin/wifi_blinky.rs)を参考に実装しています
## 環境構築
* [公式サイト](https://www.rust-lang.org/ja/tools/install)の手順に従い、Rustをインストール
* クロスコンパイルをするため、以下のコマンドでターゲットを追加
```sh
rustup target add thumbv6m-none-eabi
```
* 必要なツールをCargoでインストール
```sh
cargo install elf2rf2-rs flip-link
```
## 実行方法
* Raspberry pi pico w のBOOTSELボタンを押したままPCと接続し、以下のコマンドを実行
```sh
cargo run --release
```

## 説明
Raspberry pi pico w のオンボードLEDは、RP2040チップではなく、WiFiチップであるCYW43439のGPIOに接続されています。
また、RP2040とCYW43439は通常のSPIではなく、半二重通信での特殊なSPIで接続されています。
そのため、以下の2点のクレートを利用してpico wでのLチカを実行しています。
* **[cyw43](https://crates.io/crates/cyw43)**：cyw43のドライバ
* **[cyw43-pio](https://crates.io/crates/cyw43-pio)**：PIOを利用し半二重通信のSIPをエミュレーション

また、[ブログ](https://scrapbox.io/tetsutalow-memo/Rust%E3%81%AE%E3%83%99%E3%82%A2%E3%83%A1%E3%82%BF%E3%83%AB%E9%96%8B%E7%99%BA%E3%82%92Raspberry_Pi_Pico_W%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%82%84%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%8B)でも説明しています。
