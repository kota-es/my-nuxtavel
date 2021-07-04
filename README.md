## 環境構築
### 下記1~5を続けて実行する
1. プロジェクトクローン
    1. mkdir my-nuxtavel（任意のディレクトリ名）
    2. cd my-nuxtavel
    3. git clone https://github.com/kota-es/my-nuxtavel.git .
    4. docker-compose.ymlの38行目`command: yarn dev`をコメントアウト
    5. docker-compose up -d --build
2. laravelモジュールインストールなど
    1. cp backend/.env.local backend/.env
    2. docker-compose exec backend bash
    3. composer install
    4. exit
3. Nuxtモジュールインストールなど
    1. docker-compose exec frontend sh
    2. yarn
    3. exit
4. 再起動
    1. docker-compose down -v
    2. `command: yarn dev`のコメントアウトを外す
    3. docker-compose up -d --build
5. 通信確認
    1. http://localhost:3000/ にアクセスし、「APIテスト」ボタンが表示されることを確認
    2. 「APIテスト」ボタンをクリックすると、「success!! this is a message from laravel」が表示されることを確認

## コンテナ起動・終了
- 起動：`docker-compose up -d --build`
- 終了：`docker-compose down -v`