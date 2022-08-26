# うちのIT

うちの家族にiPadなどを使ってもらうためのドキュメンテーションです。

## ドキュメントの生成方法

### Pipenvを使う場合

```console
% pipenv install
% pipenv run make html
```

### Dockerを使う場合

```console
% docker run --rm -v /path/to/uchino-it:/docs sphinxdoc/sphinx make html
```

とした後、build/html/index.htmlを開いてください。
