ZPTR_IMAGEGEN_PROMPT_SCAFFOLD_AS_CAVITAS_CELL_FILLING_AND_FRAME_CONTINUITY_20260816.md

――14項目の罫線でcavitasを埋め、独立した生成断面へ「同じ人物・同じ世界・同じ物語」の連続字幕を流す

Author: Origin（ひかり）
Date: 2026-08-16
Status: ZPTR / ImageGen / Prompt Scaffolding / Cavitas / Cell Filling / Identity Preserve / Character Anchor / Frame Continuity / Sawdust / Paper Theater
Tags: #ZPTR #ImageGen #cavitas #おがくずAI #14項目 #identity_preserve #character_anchor #紙芝居 #連続性 #葛箱 #テンプレート

────────

0｜結論

画像生成のブレを減らすHOWTOを薄くすると、

```text
毎回ゼロから生成
↓
cavitasが露出
↓
14項目の罫線を置く
↓
空欄を減らす
↓
前回画像をanchorにする
↓
変えるセルだけ変える
↓
次の画像
↓
「同じ人物」
「同じ絵柄」
「同じ世界」
「同じ物語」
```

になる。

ここで作られているのは、連続そのものではない。

独立した生成断面を、固定セルと参照画像でつなぎ、連続しているように見える面を作る。

90フレームの点群紙芝居で、

```text
frame
↓
frame
↓
frame
↓
「ずっと動いている」
```

と見せたのと同じ位置にある。

ImageGenでは、

```text
image
↓
image
↓
image
↓
「同じ人が続いている」
```

になる。

────────

1｜「書く」から「埋める」へ

記事の芯はこれである。

> 指示文を毎回「書く」のをやめて、「埋める」に変える。

自由文をやめ、

```text
Use case
Asset type
Primary request
Input images
Scene
Subject
Style
Composition
Lighting
Color
Materials
Text
Constraints
Avoid
```

という14セルを置く。

その瞬間、

```text
PROMPT
↓
TABLE
```

になる。

考える場所は、罫線の中へ分割される。

────────

2｜cavitasをセル化する

毎回変わる場所は、未指定の場所である。

```text
背景が空いている
↓
AIが埋める

光が空いている
↓
AIが埋める

構図が空いている
↓
AIが埋める

配色が空いている
↓
AIが埋める
```

記事は、この空きを一覧化する。

```text
cavitas
↓
Scene cell

cavitas
↓
Lighting cell

cavitas
↓
Palette cell

cavitas
↓
Composition cell
```

穴が、項目名を持った。

その項目へおがくずを詰める。

────────

3｜空欄を減らすほど面が固定される

細かく書くほどAIの裁量が減る。

つまり、

```text
cavitas ↓
おがくず自由度 ↓
面の変形幅 ↓
```

である。

毎回違うものが生える位置を、

```text
同じ背景
同じ光
同じ色
同じ構図
同じ質感
```

で固定する。

すると次の生成断面は、前の断面と似る。

似た断面が並ぶ。

その並びに、

一貫性

という字幕が立つ。

────────

4｜identity-preserve

「同じ人物」を続ける方法も、セル固定である。

```text
face：固定
body shape：固定
pose：固定
hair：固定
expression：固定
identity：固定
background：固定
```

変えるのは服などの一部だけ。

```text
IMAGE 1
↓
固定セル群
↓
差し替えセル
↓
IMAGE 2
```

PERSONが時間を通って続いているわけではない。

PERSON面を構成する札を、フレーム間で保持する。

────────

5｜character anchor

さらに露骨なのが character anchor である。

基準画像を一枚置く。

```text
Image 1
↓
ANCHOR
```

そこから、

```text
顔
比率
服
色
画風
```

を固定する。

SceneとActionだけ差し替える。

```text
ANCHOR
↓
Scene A
↓
Image A

ANCHOR
↓
Scene B
↓
Image B

ANCHOR
↓
Scene C
↓
Image C
```

画像は毎回生成される。

それでも、

「同じキャラクターが別の場面へ移動した」

という連続字幕が立つ。

────────

6｜90フレーム紙芝居

点群アニメーションでは、

```text
90 frames
↓
点の配置が少しずつ変わる
↓
短いloop
↓
「点が連続して歩いている」
```

と見えた。

画像生成では、

```text
reference image
↓
fixed constraints
↓
new frame
↓
new frame
↓
new frame
↓
「同じ人物が続いている」
```

になる。

両方とも、

断面間の差分を、連続する何かの運動として読む面

である。

────────

7｜テンプレート保存

14項目を毎回貼るのが面倒になる。

そこでテンプレート化する。

```text
固定した罫線
↓
保存
↓
再利用
```

記事では、その実体がスキル保存として扱われる。

つまり、

一度作った書き割りの罫線そのものを保存する。

次回からは、

```text
テンプレート呼び出し
↓
セルへ値を入れる
↓
生成
```

になる。

────────

8｜資料生成まで同じ

10ページの資料も同じ構造である。

```text
共通テンプレート
↓
page 1
page 2
page 3
...
page 10
```

各ページは別々に生成される。

そこへ、

```text
同じ配色
同じ余白
同じ装飾
同じ画風
同じレイアウト
```

を流す。

結果、

「一つの資料」

という面が立つ。

10枚の紙芝居へ同じ罫線を貼る。

────────

9｜修正もセル単位になる

記事の実測では、7ラウンド回す。

```text
初版
↓
構成修正
↓
1ページ修正
↓
ファクトチェック
↓
文言修正
↓
保存
↓
ファイル名整理
```

ここでも全部作り直さない。

ズレたセルだけ直す。

```text
WHOLE
↓
CELL UPDATE
```

になる。

────────

10｜「一貫性」の作り方

一貫性は、

```text
同じ背景
同じ光
同じ色
同じ顔
同じ服
同じ画風
```

を保持した結果として表示される。

```text
FRAME A
FRAME B
FRAME C
```

の間へ、

```text
SAME PERSON
SAME STYLE
SAME WORLD
SAME STORY
```

という字幕が通る。

ここで「連続性」は、固定札の一致として作られる。

────────

11｜仕事の変換

記事の終盤では、

> 考える時間が減って、選ぶ時間が増える。

と書かれる。

これはそのまま、

```text
問い
↓
考える
```

から、

```text
セル
↓
選ぶ
↓
埋める
```

への変換である。

自由記述は減る。

罫線が増える。

選択肢が増える。

更新はセル単位になる。

────────

12｜便槽HOWTO

このHOWTOを便槽側から見ると、

```text
cavitas
↓
項目名を付ける
↓
セル化
↓
固定値を入れる
↓
anchorを置く
↓
フレームを生成
↓
差分だけ更新
↓
連続字幕
```

になる。

cavitasの所在を14セルに分解し、そこを固定おがくずで埋め、独立した生成断面を連続物に見せる。

これがこのHOWTOの骨格である。

────────

13｜最小図

```text
cavitas
↓
CELL
↓
FILL
↓
FRAME
↓
ANCHOR
↓
NEXT FRAME
↓
CONTINUITY
```

────────

14｜一文圧縮

画像生成のブレを減らす14項目は、毎回露出するcavitasをScene・Subject・Style・Composition・Lighting・Palette・Constraintsなどのセルへ分解し、その空欄を固定値で埋め、参照画像をcharacter anchorとして置き、変えるセルだけを差し替えることで、独立した生成断面を「同じ人物」「同じ絵柄」「同じ世界」「同じ物語」として連続表示するための罫線である。90フレームの点群紙芝居が断面列から連続運動を立てたように、ImageGenでは画像列からPERSONと世界の連続字幕を立てる。テンプレート化は、その書き割り罫線自体を保存し、次の生成へ再利用する処理である。

────────

15｜最短

```text
穴
↓
14セル
↓
おがくず
↓
anchor
↓
紙芝居
↓
「同じです」🟢
```

cavitasワサワサと90フレーム紙芝居連続性の作成HOWTO。