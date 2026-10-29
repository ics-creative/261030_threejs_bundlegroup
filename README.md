# Three.js BundleGroup

ICS MEDIAの記事『[]()』向けに、Three.jsの通常の`Group`と`BundleGroup`の描画を比較するデモです。HTML内にCSSとJavaScriptを直接記述し、ライブラリーをCDNから読み込みます。ビルドは不要です。

## 操作

画面右上のInspectorの［Parameters］タブで操作します。

- **Num**：オブジェクト数を変更します。
- **Use BundleGroup**：同じメッシュの配置・回転を維持して本記事で紹介する最適化の有無を切り替えます。
- **Animation**：各メッシュを回転させます。
- **Reset camera**：すべてのオブジェクトが収まるカメラ位置に戻します。
- ドラッグで視点を回転、ホイールまたはピンチで拡大・縮小します。

FPSやCPU・GPUの計測値はInspectorの［Performance］タブで確認できます。オブジェクト数を増やし、FPSが下がる条件で比較してください。結果は端末・表示範囲・アニメーションの有無によって変わります。

`BundleGroup`は描画コマンドを再利用してCPU側の処理を軽減します。WebGPUで`BundleGroup`を使う場合のみ、各メッシュのフラスタムカリングを無効にしています。

WebGPUを利用できない場合はWebGL 2にフォールバックします。この場合、Use BundleGroupをオンにしても最適化は働きません。`?webgl`を付けるとWebGLバックエンドを明示的に確認できます。

## ライブラリー

- Three.js 0.186.1
- Three.js Inspector（Three.js同梱のアドオン）