# 入学者出身地分析ダッシュボード

学校基本調査「出身高校の所在地県別 入学者数」のデータを  
ブラウザで可視化するツールです。

## ファイル構成

```
estat_app/
├── index.html           ← ブラウザで開くダッシュボード
├── fetch_estat_data.py  ← e-Stat APIからデータを取得するスクリプト
├── estat_data.json      ← データファイル（※最初はサンプル）
└── README.md            ← この説明
```

## 使い方

### Step 1: e-Stat APIキーの取得

1. https://www.e-stat.go.jp/mypage/user/preregister でユーザー登録
2. ログイン後、マイページ → API → アプリケーションIDの取得

### Step 2: 実データの取得

```bash
cd estat_app
python fetch_estat_data.py
```

初回実行時にAPIキーの入力を求められます。  
キーは `estat_api_key.txt` に保存され、次回以降は自動読み込みされます。

### Step 3: ダッシュボードの利用

`index.html` をブラウザで開くだけで動作します。  
※ローカルファイルからJSONを読む関係で、一部ブラウザでは  
ローカルサーバーが必要な場合があります。その場合：

```bash
python -m http.server 8000
```

で `http://localhost:8000` にアクセスしてください。

## 各学部への配布方法

1. `estat_app` フォルダごと共有フォルダに置く
2. 各学部に `index.html` のパスを案内する
3. または `python -m http.server` で学内LANに公開

## データ更新

毎年度、学校基本調査の確報が出たタイミング（12月頃）で  
`python fetch_estat_data.py` を再実行すれば最新データに更新されます。

## 機能

- **概要タブ**: KPI、出身地上位ランキング、九州内訳、経年推移グラフ
- **県間比較タブ**: 長崎県高校出身者の進学先比較、九州各大学のクロス集計
- **詳細テーブルタブ**: 全都道府県の入学者数・構成比

## 出典

政府統計の総合窓口（e-Stat） https://www.e-stat.go.jp/  
学校基本調査 統計表ID: 0003073924
