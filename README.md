# うちのIT

うちの家族にiPadなどを使ってもらうためのドキュメンテーションです。

## ドキュメントの生成方法

### Pipenvを使う場合

```console
% pipenv install
% pipenv run make html
```

一連のPortable Object Template/Portable Object/HTMLを作る手順は次

```console
% pipenv run make gettext
% pipenv run sphinx-intl update --language=ja
```

できたPOの翻訳をした後、

```console
% pipenv run make html -e SPHINXOPTS='-D language="ja"'
```

### Dockerを使う場合

```console
% docker run --rm -v /path/to/uchino-it:/docs sphinxdoc/sphinx make html
```

とした後、build/html/index.htmlを開いてください。
