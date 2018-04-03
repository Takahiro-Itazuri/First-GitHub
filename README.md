---
# 初めてのGitHub
---
### GitHubの事前知識
#### 1. ローカルリポジトリとリモートリポジトリ
<Font color="red">リポジトリ</Font>とはファイルやディレクトリの<Font color="red">状態を保存する場所</Font>である。
変更履歴などを管理したいディレクトリなどをリポジトリの管理下に置くことで、そのディレクトリ内のファイルなどの変更履歴を記録することができる。  
そしてローカルリポジトリとは自分のパソコン上にあるリポジトリで、リモートリポジトリとはインターネット上にあるリポジトリである。
#### 2. コミットとプッシュ
<Font color="red">コミット(commit)</Font>とは、ファイルの追加や変更の履歴を<Font color="red">リポジトリに保存すること</Font>である。  
<Font color="red">"プッシュ(push)</Font>とは、ファイルの追加や変更の履歴を<Font color="red">ローカルリポジトリからリモートリポジトリの管理下にアップロードする</Font>ための操作である。
#### 3. ブランチ
<Font color="red">ブランチ(branch)</Font>とは履歴の流れを分岐して記録していくものである。GitHubではブランチを利用することでそれぞれが追加でプログラムを組み、再び統合(merge)することで共同研究をすることができる。


### GitHubの作業の流れ
##### 1. リポジトリの作成(git init)、または複製(git clone)する
##### 2. ファイルの作成(touch)、編集を行う
##### 3. ファイルの作成、変更、削除をgitのインデックスに追加(git add)
##### 4. 変更結果をローカルリポジトリにコミットする(git commit)
##### 5. ローカルリポジトリをプッシュして、リモートリポジトリに反映させる(git push)  
以上の1~5の作業について詳しく説明する。  
まず自分のファイルやディレクトリの状態を保存するためのリポジトリを作成（または複製）し、初期化する。そして、そのディレクトリにファイルを作成し、編集する。次に、ファイルの変更内容をgitのインデックスに追加する。ここでインデックスとはタスクのようなもので、このインデックスに変更内容を一時的に追加する。保存したい変更内容を追加し終えたら、インデックスをリポジトリにコミットすることで、変更が保存される。このインデックスをローカルリポジトリに保存したあと、今度はリモートリポジトリにプッシュする。  
以上がGitHubで行う作業である。
### GitBashの使い方
前節で説明した作業を行うためにGitBashを用いる。
まずは変更内容を保存したいフォルダを作成し、移動する。  
<pre><code>$ mkdir filename  
$ cd filename </code></pre>   
次にリポジトリを作成し、初期化する。  
<pre><code>$ git init</code></pre>  
そしてファイルの作成と編集をする。  
例：README.mdの作成  
<pre><code>$ touch README.md</code></pre>  
次にインデックスに保存したい変更内容を追加する。  
<pre><code>$ git add --all</code></pre>  
そしてローカルリポジトリにコミットする。  
<pre><code>$ git commit -m "initial commit"</code></pre>  
次にアップするリモートリポジトリのアドレスを指定する。originにURLを代入するイメージ。  
<pre><code>$ git remote add origin https://github.com/(username)/(repository_name)</code></pre>
最後にリモートリポジトリにプッシュする。  
<pre><code>$ git push origin master</code></pre>    
以上でGitHubにアップロードが完了！

<h3> 変更内容をアップロードするとき</h3>
変更内容をアップロードするときは、すでにリポジトリは作成してあり、またアップロードするURLは指定してあるので、上の作業をすべてする必要はない。  
つまり、インデックスにaddして、ローカルリポジトリにcommitし、リモートリポジトリにpushするだけでよい。  
<pre><code>$ git add --all  
$ git commit -m "second commit"  
$ git push origin master</code></pre>  

### README.mdについて
README.mdとは<Font color="red">マークダウン記法</Font>で書かれた文書のこと。マークダウン記法とはHTMLの簡易版のようなものである。HTMLほどの機能はなくても、ある程度のことが非常に簡単な書き方で書くことができる。そして、これをアップロードするとHTML文書としてきちんと読み取ってくれる代物。詳しいマークダウン記法については[こちら](https://github.com/Takahiro-Itazuri/Atom)を参照してください。

<h3>プロキシの設定</h3>

<p>大学にいる間はプロキシの設定が必要かもしれないです．以下の情報を打ち込んでください．</p>

<pre><code>
$ git config --global http.proxy http://your-proxy.jp:8080
$ git config --global https.proxy https://your-proxy.jp:8080
</code></pre>

<p>家で使う用に設定を戻す時は以下</p>

<pre><code>$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
</code></pre>

<h3>特定ファイルの除去(.gitignoreを使う)</h3>

<p>.exeや.objといったファイルなどアップロードする必要のない場合は，.gitignoreファイルを生成して，中身を逐次書き加えていく．</p>


### GitHubで数式を表示させる方法
##### 1. Atomに"markdown-preview-plus"と"mathjax-wrapper"をインストール
##### 2. Google Cromeの拡張機能"GitHub with MathJax"を導入
Atomにはパッケージをダウンロードする機能がある．[packages]->[settings view]->[install packages/themes]の順番で選択していくと，検索画面が出てくる．そこで，"markdown-preview-plus"と"mathjax-wrapper"を検索して，インストールする．プレビューにはデフォルトで"markdown-preview"が用いられているため，こちらをオフにする必要がある．そこで，[packages]->[settings view]->[manage packages]の順番で選択していくと，再び検索画面が出てくる．そこで，"markdown-preview"と検索して，[disable]を選択するとオフにできる．実際に数式を書くときには，数式を一行に書くときは"$$"で囲む．インラインで書くときは"$"で囲むとTeX形式の数式が書けるようになる．これをGitHubにpushしても、実は数式で表示されない．そこで，[GitHub with MathJax](https://chrome.google.com/webstore/detail/github-with-mathjax/ioemnmodlmafdkllaclgeombjnmnbima)に行って，"Chromeに追加"をすると，ようやくネット上で数式が表示される．
