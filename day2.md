# keynote

- andrey vlasovskikh
    - pycharm, ideavim, typing(pep484 port)
- what's new in 3.6
    - formatted string
    - variable annotation
- type hints
    - 小さいプロジェクトでrewriteする必要はない
    - typingでpython2にportされているのでpython2->python3にportするのに使える
        - e.g.) dropbox
- async-await
    - django/flaskはblocking i/oなので注意
    - cpu boundな処理はさせない

# you might not want async

- bimetekというMonitoring as a Serviceを作っている
- 小さいパーツをasyncにする
- parallelismではない
- testが難しい
- テスト毎に独立させるためにnew_event_loopしたほうがよい
- async.waitとasync.gatherがほぼ同じ機能?
- golangのほうがだいぶ今はこなれている

# TensorFlow

- 1500以上のプロジェクトでDNNモデルを使っている

# module import

- https://docs.google.com/presentation/d/1YBesU-B8a5VrNvS7OiWzA6bXH7e7SZbl9kncPsjVU2s/edit#slide=id.g16c4861ecf_1_95
- python3以降だとsys.meta_path = {}とするとimportできなくなる
- python2.2以前は__import__を置き換えるhackしかなかった

# Database Driver

- https://gist.github.com/nakagami/bfbe98d62377f3f4554121ab161ae8c9
- pep249
- read only cursor だけ実装すれば許される
- デバッグのために中継スクリプトを書くと良い

