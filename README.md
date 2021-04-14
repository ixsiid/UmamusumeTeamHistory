# Vue project template


# Github pagesでの公開
デフォルトではカスタムドメイン利用を想定している
デフォルトURL https://(user).github.io/(repository)/ での公開をするときは vue.config.js に下記を追加する

```javascript: vue.config.js
....
module.exports = {
  ....
  publicPath: "./",
  ....
};
