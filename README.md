# pico-w-blinky
raspberry pi pico w の オンボードLEDでLチカをするプロジェクト
https://github.com/embassy-rs/embassy/blob/main/examples/rp/src/bin/wifi_blinky.rs を参考に実装しています
## 環境構築
* Rustのインストール（https://www.rust-lang.org/ja/tools/install）
* クロスコンパイルをするため、以下のコマンドでターゲットを追加
```
rustup target add thumbv6m-none-eabi
```
* 必要なツールをCargoでインストール
```
cargo install elf2rf2-rs flip-link
```
## 実行方法
* Raspberry pi pico w のBOOSTSELボタンを押したままPCと接続し、以下のコマンドを実行
```
cargo run --release
```

## 説明