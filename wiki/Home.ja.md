# Nexus Benchmark Token Studio

**Version 1.0.1**

学習処理の時間、有効なトークン数、評価記録を明示して測定します。

**[ブラウザーで試す](https://rdunbar01.github.io/Nexus-Benchmark-Token-Studio/Nexus_Benchmark_Token_Studio_v1_Browser.html)** · [デスクトップ用コンポーネントをダウンロード](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1) · [README](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/README.md)

試用ページでインターフェースを確認し、**Check WebGPU adapter** を選択してください。Python は不要です。ブラウザーのベンチマークは一時的なスクラッチモデルと合成トークンを使うため、このテストにモデルやコーパスのダウンロードは必要ありません。

ネイティブパッケージ 1.0.1、ブラウザー版 1。

## 主な機能

- 合成トークンと一時的なスクラッチモデルを使うブラウザーベンチマーク。
- 対応するネイティブ処理向けのインストール型 PyTorch テスト。
- ウォームアップ、学習、評価、生成を分けた測定結果。
- パディングを有効トークンに数えず、設定の比較用に出力できる記録。

## 技術的な貢献

小規模モデルの開発に向けた再現可能な測定ワークフローです。合成データの速度テストと、読み込んだモデル・コーパスの評価を区別し、毎秒トークン数がどの処理を測った値か明確にします。

## 単一 HTML ファイルを使う理由

ブラウザー版は、インターフェース、JavaScript、CSS、WGSL カーネルを単一の HTML ファイルにまとめています。ビルド手順や実行時の CDN を必要とせず、オンラインで開き、リンクを共有し、内容を確認しやすくするための構成です。ファイルに含まれるのはブラウザー用エンジンであり、モデルの重みやネイティブ PyTorch バックエンドではありません。

HTTPS 上で WebGPU 対応ブラウザーを使用してください。この合成ベンチマークは GGUF ローダーやコーパス評価ではありません。実行時のネットワーク要求、ネイティブのハードウェア監視、ローカルサーバーとのブリッジは無効です。モデルを読み込んでコーパスを処理するには、完全なインストール版と対応するネイティブ PyTorch 経路が必要です。

[English](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ko)

## Python とネイティブ実行環境の要件

- **推奨インタープリターは標準の64ビット CPython 3.12 です。** インストーラーの案内範囲は **Python 3.11–3.14** ですが、起動用スクリプト自体はこの範囲を強制しません。他のバージョンで開けても、ネイティブバックエンドの互換性を証明したことにはなりません。
- **新しい AMD 実行環境のインストールには、Windows 11 25H2 上の標準64ビット CPython 3.11–3.14 が必要です。free-threaded 版は対象外です。** 既存環境はこのインストール条件の確認前にテストされ、実行テストに成功した場合のみ再利用されます。Python とインストール済み PyTorch wheel の対応が必要です。それ以上の Python バージョン互換性は認定していません。
- 同梱のネイティブテストは **PyTorch 2.14.0+rocm10.1.0**、HIP、設定された RX 7900 XT/XTX を要求し、FP32 の順伝播・逆伝播の値が有限であることを確認します。このパッケージは Python、AMD ドライバー、コンパイラーの前提条件をインストール・変更しません。[AMD 公式互換性表](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html)を確認してください。

これらはインストーラーと実行環境の条件であり、実機 Windows・WebView2・Radeon やフルモデルの検証完了を意味しません。テスト成功はすべての精度・コンパイル方式・処理負荷を保証しません。


## 目的

一時的なモデルの学習と、対応するネイティブ処理の性能を測定します。ブラウザー版は使い捨てのモデルと合成トークンを使うベンチマークであり、汎用の推論ローダーや読み込んだモデルの評価器ではありません。

## エディションの選択

### ブラウザー版

HTTPS 上で WebGPU 対応ブラウザーを使用してください。この合成ベンチマークは GGUF ローダーやコーパス評価ではありません。実行時のネットワーク要求、ネイティブのハードウェア監視、ローカルサーバーとのブリッジは無効です。モデルを読み込んでコーパスを処理するには、完全なインストール版と対応するネイティブ PyTorch 経路が必要です。

### インストール版

[1.0.1 パッケージ](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1)のすべてのファイルを、配布時の構成を保って一緒にダウンロードしてください。番号付きのすべての `.nxd` データパーツを [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/Start_Nexus.py) と同じ場所に置き、対応する Python で `python Start_Nexus.py` を実行します。同意前に[対応するガイド](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/README.md)とインストール内容の概要を確認してください。各 `.nxd` パーツは **10,000,000 バイト以下**、インストール前の配布ファイルは1個あたり **20,000,000 バイト未満**です。アーカイブ全体、復元後のアプリ、インストール済みファイル、ダウンロードするモデルはこれを超える場合があります。異なるリリースを混在させないでください。ネイティブ PyTorch の設定・テストはインストール版の機能であり、HTML 単体の試用版の機能ではありません。

## 測定結果と制限

CPU 回帰テストや静的解析・DOM テストは、実機の Windows/Radeon/WebGPU 検証ではありません。モデル、コーパス、コンテキスト、バッチ、精度、バックエンドが等しい条件で比較してください。学習・回復、プロンプト処理、トークン生成の速度は別々の指標です。すべての環境での互換性や最高速度を保証しません。

## 利用条件とクレジット

Rich Dunbar / Nexus Emerging Technology. Nexus が権利を持つものについては、個人利用および社内での商用テスト・評価が許可されます。配布、改変、本番環境への導入、その他の商用利用には、明示的な書面による同意が必要です。第三者のライセンスと既に付与された権利は変更されません。 [ライセンス](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/LICENSE) · [評価用の追加許諾（英語）](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
