---
date: 2026-11-05T19:00:00+03:00
title: Построение kD-дерева на Rust + визуализация с помощью WASM
price: 0
networkly_id: 7109
description: Разбираемся, как создавать нетривиальные ссылки и рисовать с помощью WASM.
vkvideo: oid=-241467855&id=456239023&hash=9e4b2971b23606d3&hd=3
youtube: joZ_m2oH6oo?si=AD5OutCJknCpjdjo
educators:
  - mark-shevchenko
---

Как быстро найти ближайшие магазины на карте?
С помощью kD-дерева — структуры данных, благодаря которой работают геоинформационные системы и игровые движки.

Мы реализуем kD-дерево на языке Rust и визуализируем его в браузере.

Вы узнаете:
* как завладеть одним элементом массива, не трогая остальные
* почему `f64` не реализует `Ord` и как с этим справиться
* как создавать циклические ссылки `Rc` и `Weak`
* как работает WASM
* как генерировать случайные `f64` из сырых байтов

Ведущий — **Марк Шевченко**, программист с 30-ти летним стажем. Когда-то создал первый сайт КАМАЗА и писал игры в Акелле.

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

* [GitHub](https://github.com/markshevchenko/kdtree)
