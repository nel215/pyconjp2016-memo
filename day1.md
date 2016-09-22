# Pythonを含む多くのプログラミング言語を扱う処理フレームワークとパターン

## エンジニアリングと再利用

- 知識体系や基盤を押さえておくことが大切
- アドホックなベストプラクティスはリスクが高い
- SWEBOK
- 参考文献: エンジニアリング基礎知識体系とISO標準

## 多言語向けツール

- OCCF
    - ASTにテストカバレッジ測定用コードを埋め込む
- UNICOEN
    - OCCFを汎用的にしたもの

## フレームワークからデザインパターン

- やみくもにデザインパターンを使わない
- 問題の本質をとらえる
- 品質との関係を押さえる
- 設計原則を押さえる
- リファクタリングをする

# Tiny DAW

##  音声の多重再生

- PCMバイトストリームが非同期に入ってくる
- 自分で実装すると大変なのでSDLのライブラリ(pygame)を使う
- 内部的にはchannelで管理されている

# Chat Bot made by chainer

## 対話の価値

- 連続性
- インタラクティブ
- ユーザー体験
    - 対話データが少なくても良いのでアプローチしやすい
    - ユーザーに対するハードルを下げる

## 話題の分類

- 話題を先に予測できれば学習データが少なくても良さそうという仮説
- 前段にWikipedia Entity Vectorを使う
    - wikipediaのlinkを考慮したword2vec
- そのあとでクラスごとの平均ベクトルを階層クラスタリングしてマージ

# パッケージの話

- PyPA
    - パッケージングツールをメンテするグループ
- setuptools
    - 配布物を作る
- virtualenv
    - python環境を仮想化する
    - python3.3以降ではpyvenvが同梱
- pip
    - インストーラ
    - sdist, wheel形式が扱える
- wheel
    - wheel形式のパッケージを作成するツール
    - pep 427
- wheelはデフォルトで入らないので入れる必要がある
- ubuntu(debian?)のpyvenvが謎のパッケージデータを作成されるのでvirtualenvしたほうが良い
- PYTHON_PATH
    - sys.pathに追加される
- site-packages/user-site-packages
    - サードパーティ製ライブラリのインストール先
    - .pthファイルにファイルパスを書いておくとsys.pathに追加される
- distutils
    - setup.pyで使うsetup関数の大本
- pep513 linux向けwheel
    - manylinux1という最低限のライブラリが入っていると想定できるタグができた
    - CentOS 5.11相当
    - auditwheelを使うとmanylinux1のチェックと依存ライブラリの同梱してファイル名を書き換えてくれる
        - C拡張を含んでいる場合に便利
    - dockerイメージも用意されている
- sdist
    - setup.py install ができればsdist?
        - 関係ない
    - pepでは特に決まっていなかった
    - pep518で決まった
        - pyproject.toml

# 確率的NN

- 確率的ニューロンの計算は単純なBPではなくなるがテクニックで実装できるという話
    - e.g.) 正規分布、二項分布
- サンプリングした値を次の層にFFする

## likelihood-ratio method

- 強化学習のreinforceと同じ
- lossが高くなる確率を下げるように学習する
- 極限が購買に一致することが証明されている
- varianceが高いのが問題
    - bを先に加えておく
    - よく使われている
- 式変形と勾配計算の対象の限定をうまくコード上で行う

## reparameterization trick

- 特定の属に対して使える
- 確率ユニットをノイズだけ別ユニットにして決定的にする
- LRに比べてvarianceが低い
