## 外部APIの呼び出しのミニレポート
### Q3-1. 郵便番号APIについて説明せよ。
* エンドポイントと機能
https://zipcloud.ibsnet.co.jp/api/search
* このAPIは、日本の郵便番号（例：1000001）から、該当する都道府県・市区町村・町域などの住所情報を検索できるAPIである。
* リクエストとレスポンスのフォーマット
* リクエスト:
* https://zipcloud.ibsnet.co.jp/api/search?zipcode=1000001
* レスポンス（JSON形式）:
{
  "message": null,
  "results": [
    {
      "zipcode": "1000001",
      "address1": "東京都",
      "address2": "千代田区",
      "address3": "千代田",
      "kana1": "ﾄｳｷｮｳﾄ",
      "kana2": "ﾁﾖﾀﾞｸ",
      "kana3": "ﾁﾖﾀﾞ"
    }
  ],
  "status": 200
}

### Q3-2. 各自で調査したAPIについて説明せよ。
* APIの名称と参照URL
API名：Open-Meteo API（天気予報API）
参照URL：https://open-meteo.com/
* エンドポイントと機能
緯度・経度から現在の天気（気温、風速など）を取得するエンドポイント：
https://api.open-meteo.com/v1/forecast?latitude={緯度}&longitude={経度}&current_weather=true
また、都市名から緯度経度を取得するために、次のエンドポイントを使用した：
https://geocoding-api.open-meteo.com/v1/search?name={都市名}
* リクエストとレスポンスのフォーマット
位置情報API（例）：
リクエスト：
https://geocoding-api.open-meteo.com/v1/search?name=Tokyo
レスポンス（抜粋）：
{
  "results": [
    {
      "name": "Tokyo",
      "latitude": 35.682839,
      "longitude": 139.759455
    }
  ]
}

天気API（例）：
リクエスト：
https://api.open-meteo.com/v1/forecast?latitude=35.68&longitude=139.76&current_weather=true
レスポンス（抜粋）：
{
  "current_weather": {
    "temperature": 23.5,
    "windspeed": 5.4,
    "winddirection": 120,
    "weathercode": 1,
    "time": "2024-06-01T12:00"
  }
}

### Q3-3. 感想
* 今回の課題で苦労したこと
今回の課題で苦労したこと
初めて扱うAPIだったため、エンドポイントのURL構造やレスポンス形式を調べて理解するのに時間がかかった。
* 演習を通して理解できたこと
フォームから取得したデータをAPIに渡し、非同期通信（fetch）で結果を取得し、ページに表示する一連の流れが理解できた。
* Web APIの利便性や課題など
Web APIは自分で大量のデータを持っていなくても、外部からリアルタイムに情報を取得できる点が非常に便利だと感じた。
