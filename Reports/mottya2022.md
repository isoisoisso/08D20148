# 課題1：デザインパターン個別レポート
## Flyweightパターン
### ・概要
複数の箇所で同じ内容のインスタンスを使用する場合、使用する回数分インスタンスを生成すると、メモリの使用量やインスタンス生成に必要な時間が多くなりプログラム全体の動作が遅くなることが考えられる。Flyweightパターンは、このような事態を防ぐことを目的としている。具体的には、同じ内容のインスタンスを使用する際、複数個インスタンスを生成するのではなく、一つのインスタンスを共有することでメモリ使用量やかかる時間を抑えている。
### ・クラス図とその構成要素
Flyweightパターンは主に、FlyweightFactory、Flyweight、Clientの3つのクラスからなる。
- FlyweightFactory
- Flyweight
- Client

![クラス図](https://www.plantuml.com/plantuml/png/SoWkIImgAStDuNBBgInFpKpFA75BJ2x9BwfKoDVLLO0BSZddPARcbIZ0XH3gh1HAYrEB5UomA478OUf2gC8ccPvQ0XVLqEH2Dj4tjIGZFmKew92Qbm9qEG00 "クラス図")
### ・具体例
    