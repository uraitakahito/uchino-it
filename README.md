# うちのIT

うちの家族にiPadなどを使ってもらうためのドキュメンテーションです。

## ドキュメントの生成方法

### Pipenvを使う場合

Dockerイメージを作成してコンテナを動かします。

```console
% PROJECT=$(basename `pwd`)
% docker image build -t $PROJECT-image . --build-arg user_id=`id -u` --build-arg group_id=`id -g`
% docker container run -it --rm --init --mount type=bind,src=`pwd`,dst=/app --name $PROJECT-container $PROJECT-image /bin/zsh
```

Docker上でSphinxを実行します。

```console
$ poetry install
$ poetry run make html
```

一連のPortable Object Template/Portable Object/HTMLを作る手順は次

```console
$ poetry run make gettext
$ poetry run sphinx-intl update --language=ja
```

できたPOの翻訳をした後、

```console
$ poetry run make html -e SPHINXOPTS='-D language="ja"'
```

PDFを出力する場合

```console
$ poetry run make latexpdf -e SPHINXOPTS='-D language="ja"'
```

### PublicなDockerイメージを使う場合

```console
% docker run --rm -v /path/to/uchino-it:/docs sphinxdoc/sphinx make html
```

とした後、build/html/index.htmlを開いてください。
