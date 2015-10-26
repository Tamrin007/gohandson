# STEP 7: 画像を縮小／拡大しよう

## golang.org/x/imageパッケージ

`golang.org/x/image`パッケージは、標準パッケージの`image`パッケージより機能を増やしたパッケージです。
特に`draw`パッケージは、スケールなどの機能が追加されています。

`golang.org/x`以下にあるパッケージは、サブプロジェクトとしてGoチームによって保守されています。
`image`以外にも、`golang.org/x/net`など便利なパッケージがありますので、一度覗いてみると良いでしょう。

このステップでは、`golang.org/x/image/draw`パッケージを使用しますので、`go get`しておきましょう。
以下の通り、`go get`を実行すると、`src`と`pkg`以下に`golang.org/x/image/draw`がインストールされている事が分かります。

```
$ go get golang.org/x/image/draw
$ tree pkg
pkg
└── darwin_amd64
    └── golang.org
        └── x
            └── image
                ├── draw.a
                └── math
                    └── f64.a
$ ls src/golang.org/x/image/
AUTHORS         LICENSE         bmp             colornames      font            testdata        vp8l
CONTRIBUTING.md PATENTS         cmd             draw            math            tiff            webp
CONTRIBUTORS    README          codereview.cfg  example         riff            vp8
```

## 実行例

```
$ pwd
/path/to/gohandson/imgconv/ja/solution
$ GOPATH=`pwd`
$ go install step7/cmd/imgconv
$ go install tools/cmd/httpget
$ ./bin/httpget https://raw.githubusercontent.com/tenntenn/gopher-stickers/master/png/01.png > gopher.png
$ ./bin/imgconv -resize 50%x50% gopher.png gopher2.png
```