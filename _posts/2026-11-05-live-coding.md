---
date: 2026-11-05T19:00:00+03:00
title: Пишем kD-дерево на Rust и запускаем его в браузере
price: 0
networkly_id: 7109
description: Владение массивом, секреты f64, циклические ссылки Rc/Weak, WASM.
educators:
  - mark-shevchenko
---

Как быстро найти ближайшие  магазины на карте? С помощью kD-дерева — структуры данных, благодаря которой работают геоинформационные системы и игровые движки.

Мы реализуем kD-дерево на языке Rust и визуализируем его в браузере.

Обсудим:
* владение массивом
* почему `f64` не реализует `Ord`
* циклический ссылки `Rc` и `Weak`
* WASM
* генерацию случайных `f64` из сырых байтов

Как подготовиться:
* установить **rustup**
* установить таргет **wasm32-unknown-unknown**
* установить **lld**
* с помощью **cargo** установить **wasm-pack** и **sfz**

### Nix
Создайте каталог **kdtree-rust**, а в каталоге — файл **shell.nix** следующего содержания:

```nix
{ pkgs ? import <nixpkgs> { } }:
pkgs.mkShell {
    nativeBuildInputs = with pkgs.buildPackages; [
        rustup
        wasm-pack
        lld
        sfz
    ];
}
```

В каталоге запустите **nix-shell**, после этого однократно запустите:

```bash
rustup default stable
rustup target add wasm32-unknown-unknown
```

### Debian/Ubuntu

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

rustup default stable
rustup target add wasm32-unknown-unknown

sudo apt update
sudo apt install -y lld pkg-config libssl-dev

cargo install wasm-pack --locked
cargo install sfz --locked
```
