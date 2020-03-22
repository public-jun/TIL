# Docker入門

## Dockerって何？

* コンピュータ上にコンテナと呼ばれる箱を作り、そこにOSやソフトを入れてあたかも違うコンピュータのように扱えるもの

* 従来の仮想化技術(サーバ仮想化)に比べてDockerの仮想化(コンテナ仮想化)は軽量でプロセッサやメモリの消費量が少なくストレージの使用量もわずかです

* 一番の違いは __サーバ仮想化ではそれぞれのOSでそれぞれのAppを動かしているのに対して、コンテナ仮想化では仮想マシンごとにOSを立ち上げていない。__ それはそれぞれの仮想マシンがホストOSのカーネルを共有している.


## Dockerで何ができるの？

* __アプリ開発環境の構築__

* __マイクロサービスの実行環境の構築__

