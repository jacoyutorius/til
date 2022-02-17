# ssmlで応答のイントネーションを調整する

```html
<prosody pitch='low'>ごり</prosody>ようありがとうございました！
```


```
prosody

タグで囲まれた音声の音量、高さ、速さを変更します。
```

`pitch` 以外にも `rate` で細かい調整ができるが、、

```
pitchタグを使用すると、AlexaはレガシーのText-to-speechシステムを使用します。これにより、読み上げの音質が変わる可能性があります。
```

とあるように、prosodyタグを使うとレスポンスの音声が気持ちノイズが混じった感じになる。

ssmlのリファレンス

https://developer.amazon.com/ja-JP/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html#prosody

