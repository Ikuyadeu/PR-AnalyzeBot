# 環境の作成の仕方
1. 最新のnodeとnpmを用意する．Macの場合：http://umekov.hatenablog.com/entry/2016/12/03/000001

```
node -v
npm -v
```
を端末で実行して
nodeが7.7.0，npmが4.0.0以上なら成功

2. 上田のリポジトリからプロジェクトをクローンする
```
git clone https://github.com/Ikuyadeu/PR-AnalyzeBot.git
```
3. [GitHub Apps](https://github.com/settings/apps/new)を作成する．
    3.1 `GitHub App name`:好きな名前（後から変更できる）
    * `Homepage URL`:http://localhost:1410
    * `User authorization callback URL`:http://localhost:1410/auth.callback
    * `Webhook URL`:https://example.com　(後ですぐ変える)
    * `Webhook secret`:development
    * `Permissions`:全部チェック(Single fileは`.github/*`)
    * 最後の`where can this GitHub App be installed?`は`Only on this account` のまま
4. ページの一番下に行って`Generate private key`ボタンを押してxxx.pemをダウンロードして，プロジェクトのルートに置く
6. プロジェクトのルートに`.env`というファイルを作る
中身は
```
APP_ID=作ったページの右上にある４桁の数字
WEBHOOK_SECRET=development

# Uncomment this to get verbose logging
# LOG_LEVEL=trace

# Subdomain to use for localtunnel server. Defaults to your local username.
SUBDOMAIN=適当な英数字(-などの記号は使えない)
```
7. プロジェクトのルートで`$ npm install`を実行
8. プロジェクトのルートで`$ npm start`を実行
    * `https://xxxx.localtunnel.me/`というのが表示されるのでGitHub AppsのWebhookをそれに書き換える．
    * `Ctrl + C`
9. もう一度`$ npm start`
9. Appsページの右上の`install`ボタンで自分のプロジェクトにインストールする．（プロジェクトを持ってなければ作る(public推奨)）
    * `only select repository`にチェック
10. インストールしたプロジェクトでissueを作る
11. ページを再読み込みしbotが発言していたら成功

## 開発に使えるGitHub関連ページ
* https://developer.github.com/webhooks/
* https://developer.github.com/v3/pulls/

## Probot Document(English)
https://github.com/probot/probot

## Probot Sample
- [stale](https://github.com/probot/stale) - 自動でissueをClose
- [owners](https://github.com/probot/owners) - PRを送った人にownerを知らせる
