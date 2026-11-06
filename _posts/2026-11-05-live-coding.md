---
date: 2026-11-05T19:00:00+03:00
title: Пишем kD-дерево на Rust и запускаем его в браузере, Часть I
price: 0
networkly_id: 7109
description: Владение массивом, секреты f64, циклические ссылки Rc/Weak, WASM.
vkvideo: oid=-241467855&id=456239023&hash=9e4b2971b23606d3&hd=3
youtube: joZ_m2oH6oo?si=AD5OutCJknCpjdjo
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

Ведущий — **Марк Шевченко**, программист, докладчик, основатель Московского клуба программистов.

Как подготовиться:
* установить **rustup**
* установить таргет **wasm32-unknown-unknown**
* с помощью **cargo** установить **wasm-pack** и **sfz**

### Nix
Создайте каталог **kdtree-rust**, а в каталоге — файл **shell.nix** следующего содержания:

```nix
{ pkgs ? import <nixpkgs> { } }:
pkgs.mkShell {
    nativeBuildInputs = with pkgs.buildPackages; [
        rustup
        wasm-pack
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

cargo install wasm-pack --locked
cargo install sfz --locked
```

## Ссылки

* [Код проекта на GitHub](https://github.com/markshevchenko/kdtree)
