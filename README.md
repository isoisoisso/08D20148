# ソフトウェア工学レポート提出用リポジトリ  

**現在下記ドキュメントは工事中です。。。12/14の講義が終わってから、みんなで作業開始にしましょう。**

<br>
<br>
<br>

**大倉注：この手順で試すのは今年度が初めてです。バグや不明点がありましたら積極的にご報告いただけると幸いです。。。**

以下の手順説明をよく読んだ上で、次の2つの課題に取り組むこと。

1.  ディレクトリReports以下に各自講義では説明していないデザインパターンに関するレポートをMarkdown形式（テキスト形式でも可）で追加する。
2. DesignPattern.mdを全員で編集し、講義で説明したデザインパターンのまとめをつくる

〆切は2022/1/10（火）23:59。Gitコミットのタイムスタンプで判断します。
<br><br><br>

## 作業の準備
### gitのインストール
まだ自分の作業環境にgitコマンドがインストールされていない人は、以下のページなどを参考にgitをインストールする。

[Git - Gitのインストール](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)

### 自分のユーザ名を連絡する
以前の講義で説明した通り、今回のレポート提出に使うユーザ名（と学籍番号）を大倉まで連絡する。
以下、仮にユーザ名をAnonymousStudentとしたとする。

### 準備：パーソナルアクセストークンの取得（あるいは公開鍵の登録）
GitHubは、2021年にセキュリティ向上のためにパスワードアクセスを廃止した。GitHubにログインするためには、パーソナルアクセストークン（OAuth）か鍵認証が必要になっている（パスワード廃止の流れは今後多くのサービスにも広がると思われるので、慣れておくと良い。API関連のアクセスはOAuthが広く使われているし、一般的なサーバへのSSH認証は鍵認証が多い。）

アクセストークン生成の参考：https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

1. ブラウザでGitHubにログインし、Settings -> Developer settingsを開く
2. Personal access tokens -> Tokens (classic) を開く（たぶんFine grained tokenでも同じようにできる）
3. Generate new token (classic)
4. Token nameにわかりやすい名前（自分自身が識別できれば良い）をつけ、Expirationは余裕を持って60days以上（この課題提出が終わる以降）としておく
5. Select scopesから、``repo''を選ぶ
6. Generate tokenし、出てきた文字列をコピーする（**このページを離れるとコピーできない**ので、離れてしまった場合は再度作成する必要がある）

今後、**生成されたアクセストークンをパスワードの代わりに使う**。cloneやpush/pullなどのたびにトークンの入力が必要になるので、アクセストークンを安全に管理しておくこと。

ちなみに、いちいちトークンを入力しなくても良くなる方法として、公開鍵を登録してSSH接続をする方法がある（慣れてくるとこちらのほうが楽。サーバへの接続方法としてはかなり一般的なので、こちらも慣れておくと良い）。詳細はぐぐってみること。本講義では、どちらの認証方法を使っても構わない。

### リポジトリをcloneする
任意の作業ディレクトリに移動して、講義用のアカウントでリポジトリをクローンする（以下の例のアカウントは自分のものに置き換える）。

```
$ git clone https://github.com/fumio125/SELecture2022_GitReport.git
Username for 'https://github.com': AnonymousStudent
Password for 'https://AnonymousStudent@github.com': <パーソナルアクセストークン>
```

クローンしたディレクトリに移動し、リポジトリ上で表示される名前も上記のユーザ名と一致するように設定する。採点はこのユーザ名を基準に行うのでこの作業を忘れずに行うこと。

```
$ cd SELecture2022_GitReport
$ git config --local user.name "AnonymousStudent"
$ git config --local user.email "<自分のメールアドレス>"
```
* `git config --local`は現在のディレクトリにのみ有効な設定を行うためのオプション
* `git config -l`コマンドで現在の設定が確認できるので、user.nameとuser.emailが上で設定した値になっているかを確認する
<br><br><br><br><br>

## レポート提出
### 課題１：個別レポートをReports以下に追加
まず、最初の時点での作業ブランチがmainになっていることを確認する。

```
$ git branch
* main
```
この状態でReports/<ユーザ名>.mdというファイル名でレポートを作ってリポジトリに追加する。  
内容は、講義では**説明していない**デザインパターンのうちのどれかに関する簡単なまとめ。  
ファイルの中身に名前や学籍番号を記入する必要はない。

上のユーザ名の例だと、AnonymousStudent.mdというファイルをReports以下に作って、

```
$ git add Reports/AnonymousStudent.md
$ git commit -m "<任意のコミットメッセージ>"
$ git push
```
コミットメッセージの内容は何でも良いが、一般論として、更新箇所や内容がわかるようにすることが望ましい。

下の課題２でも使われている拡張子mdはMarkdown形式のファイル。記法に関しては特に難しいことはないはずなので各自で調べること。

[Markdown - Wikipedia](https://ja.wikipedia.org/wiki/Markdown)
<br><br>

### 課題２：DesignPattern.mdを共同編集
次に、課題２の作業に入る前に、競合を避けるために**ユーザ名と同じ名前の新しいブランチ**を作る。
上のユーザ名の例だと、

```
$ git branch AnonymousStudent
$ git checkout AnonymousStudent
```

この状態で、ディレクトリ直下にあるDesignPattern.mdを編集する。  
内容は第８回の講義で**説明した**デザインパターンのまとめ。  
DesugnPattern.mdに書かれたテンプレートに追記する形で、全員で協力して講義で触れた全パターンを網羅することを目指すこと。  
より詳細な説明や、違うプログラミング言語でのサンプルなどを追加する。各パターンの事例数は適宜追加して良い。

編集後は、まずリモートリポジトリにも同名のブランチを作ってpushする（上とは若干異なるので注意）。

```
$ git add DesignPattern.md
$ git commit -m "<コミットメッセージ>"
$ git push -u origin AnonymousStudent
```
この時点で編集内容はリモートのAnonymousStudentブランチに反映されるが、その内容はmainブランチには反映されないので、mainブランチを再度チェックアウトして最新版に更新した後、自分のブランチをマージする。

```
$ git checkout main
$ git pull
$ git merge AnonymousStudent
```
このとき、他の学生が編集した内容との衝突が起こると次のようなエラーが表示される。

```
Auto-merging DesignPattern.md
CONFLICT (content): Merge conflict in DesignPattern.md
Automatic merge failed; fix conflicts and then commit the result.
```
この場合はDesignPattern.mdを開いて衝突を解消し（争いを避けるために自分ではなく他人の編集を優先しましょう）、新たなコミットを行う。

```
$ git add DesignPattern.md
$ git commit -m "<コミットメッセージ>"
```
最後にpushして作業をリモートに反映させる。

```
$ git push
```
<br>

### 注意事項
* 説明はコマンドラインインタフェースを想定しているが、作業内容を正しく理解した上でGUIクライアントを使う分には問題ない。
* 採点はGitを正しく使ったかどうかと、レポート内容の両方を考慮する。
* （一応private repoではあるものの、）リポジトリのURLは外部にシェアしないこと。
* （一応private repoではあるものの、）ユーザ名やファイルの中身に、氏名・学籍番号などの個人情報を掲載しないように注意すること。
