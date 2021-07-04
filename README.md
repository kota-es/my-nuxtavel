## 環境構築
1. mkdir my-nuxtavel（任意のディレクトリ名）
2. cd my-nuxtavel
3. git clone 
4. cp backend/.env.local backend/.env
5. docker-compose exec backend bash
6. composer install
7. exit
8. docker-compose.ymlの38行目`command: yarn dev`をコメントアウト
9. docker-compose exec frontend sh
10. yarn
11. exit
12. docker-compose down -v
13. docker-compose.ymlの38行目`command: yarn dev`をコメントを外す
14. docker-compose up -d --build
15. http://localhost:3000/ にアクセスし、「APIテスト」ボタンが表示されることを確認
16. 「APIテスト」ボタンをクリックすると、「success!! this is a message from laravel」が表示されることを確認

## コンテナ起動・終了
- 起動：`docker-compose up -d --build`
- 終了：`docker-compose down -v`