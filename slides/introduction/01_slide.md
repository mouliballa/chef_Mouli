# 基礎からのChef !

<center><img src="../images/oc-chef-logo.png" height="394" width="500" /></center>
<center>OPS150-04.01 - January, 2012</center>

<center>Created and Sponsored by Opscode, Inc.</center>
<center><b>翻訳：Creationline, Inc.</b></center>

.notes These course materials are Copyright © 2010-2012 Opscode,
Inc. All rights reserved.  This work is licensed under a Creative
Commons Attribution Share Alike 3.0 United States License. To view a
copy of this license, visit
http://creativecommons.org/licenses/by-sa/3.0/us; or send a letter to
Creative Commons, 171 2nd Street, Suite 300, San Francisco,
California, 94105, USA.


!SLIDE
# 事前準備

* 開始と終了の時間ついて
* 休憩時間ついて
* 昼食について
* トイレに関する内容について
* 交通機関と駐車場について


!SLIDE
# 講師

* 氏名
* 会社名　/　グループ
* Chefやサーバ設定にかんする経験
* 連絡先の情報

.notes 連絡先には、最低限電子メールアドレスを追記する。


!SLIDE
# 参加者

* 氏名
* 会社名　/　グループ
* Chefやサーバ設定にかんする経験
* コースのゴール


!SLIDE
# コースのゴール

* Chefのツールと構造の理解
* クックブックの改造、作成、取得
* Chef Server APIでの操作
* Opscodeが使っている一般的なパターンの理解
* Opscodeの製品の理解

Chefは非常に複雑なシステムです。たとえ２週間を使って解説しても全てをカバーすることは出来ないでしょう。
このコースでは、参加者にChefの基礎と最も重要なトピックと技術、学習のための障害を説明することを目的としています。


!SLIDE
# コースに含まれない項目

全てをカバーすることはしません。特に下記の項目に関しては、このコースではカバーしません：

* 他のツールとの直接比較
* 高度な機能の詳細
* アプリケーションの開発の戦略の議論
* オープンソースのChefサーバの設定と管理


!SLIDE
# Chefの学習

このコースは、Chefの学習を促進することを目標にします。

このコースでは、頻繁に休憩して、多数のハンズオンを演習を実施増す。

もしも各セクションのトッピックに関して質問がある場合は、しばらく我慢して質問を熟成してください。いくつかの質問は後のセクションの教材の中で答えが導かれることもあるはずです。

広範な又は詳細な質問は、関連するセクションの最後か、１日の終わりか、コースの終わりで回答することがでいます。

.notes 休憩の方法は、 Pomodoros方式 (25 mins w/ 5 min
break)か、それぞれのセクション単位で休憩する方式とする


!SLIDE
# コースの学習項目

* はじめに
* とっかかり
* Chef実行の詳細
* Cookbooks, Recipes, Resourcesについて
* Chefに必要な最低限のRubyの知識
* Resourcesに関する詳細

.notes このコースでは、これらのリストに沿って、内容を論理セクションに分け、進行していきます。
講義では、内容びは、色々な詳細レベルを設定してあり、後戻りすることもあります。セクションのほとんどには、ハンズオン演習が付いており、ハンズオンの為のサーバも的供されています。


!SLIDE
# コースの学習項目

* トラブルシューティング
* Chefノード
* ロール
* Cookbooksの詳細
* 複数ノードと検索
* 追加Topics
* Chefでの開発とResourceの詳細

.notes 追加トッピクス：Data bags, Environments, LWRPs,
Plugins, Reporting。さらに今までの流れで質問された項目で、コースでカバーしていない項目。


!SLIDE
# コース終了時に完成している構成

コース終了に時は次のことが完成しています:

* OpscodeのアカウントとOpscode Hosted Chef organization (Chef Server)
* Opscode Hosted ChefをコントロールするためのWorkstationの設定
* インフラをChefコードとして管理するためのリポジトリ


!SLIDE
# ベストプラクティスについて

このコースでは、我々の考える”ベストプラクティス”を中心に説明しいきます。

Chefを使う際、多くのことがらは複数のアプローチを取ることが出来ます。今回は、その中の一つにフォーカスし、他を紹介するにとどめます。

ベストプラクティスは、主観的なものです。

Chefは自由度が高いので、開発者が望むことは大抵のことは出来てしまいます。


!SLIDE
# コースの教材について

"Chefの基礎トレーニング"に使う資料には２つのライセンスが適応されています。

* Creative Commons Attribution-ShareAlike (CC BY-SA) for slides,
  guides and notes.
* Apache License, Version 2.0 for supporting code and significant
  example code on slides.

GitHub Repository:

* [http://github.com/opscode/chef-fundamentals](http://github.com/opscode/chef-fundamentals)

.notes "重要なコードの例"は、cookbookの様なOpscodeのオープンソースプロジェクトを引用することができます。


!SLIDE
# Chef入門

* サーバ設定管理
* システムインテグレーション
* 中心ん的な概念

.notes 今まで、休憩を取っていないのならばここで５分休憩。ここまで、コースの紹介は終了です。これからChefに付いての紹介が始まります。


!SLIDE
# サーバ設定管理

"Keep track of all the stuff you do to take a system from 'bare metal'
to 'doing its job'." - Adam Jacob, Web Operations (O'Reilly, 2010)

これは色々な方法で達成できます。

* Wikiのノートのコピペ
* スクリプト化、ssh-in-a-for-loop
* 自動化フレームワーク



.notes Using an automated framework is why we're all here, after all.
.notes 結局は、自動化のフレームワークを使うことが我々がここにいる理由。


!SLIDE
# 物理的ハードウェア

ラックに備え付けられてたコンピュータがあるとします。

<center><img src="../images/bare-metal.png" /></center>


!SLIDE
# 物理的ハードウェア...Cloud?

又は、クラウドでどのようなコンピュータが必要かというアイディアがあるとします。

<center><img src="../images/bare-metal-cloud.png" /></center>


!SLIDE
# 各サーバの設定完了

全てのサーバ設定が完了し、それぞれのサーバが機能し始めたとします。

<center><img src="../images/doing-their-job.png" /></center>


!SLIDE
# システムのインテグレーション（構成管理）

正しいソフトウェアをインストールし、設定しただけのサーバ群はビジネス的な価値を生み出していません。

それらは、協調して役割を果たせるように関連づけられる必要があります。

* webサーバはロードバランサーに登録される必要があります。
* webサーバは、DBやキャッシュサーバにアクセスできるようにする必要があります。
* DBは、安定性を向上するためにクラスタを構成する必要があります。

!SLIDE
# システムのインテグレーション（構成管理）

典型的なシステムでは、このような構成は複雑です。例えば、６台を使ったシステム構成は以下のようになり、2台のDBは複雑なHAデータベースのサブシステムを構成します。

<center><img src="../images/integrated-systems.png" /></center>


!SLIDE
# システムのインテグレーション（構成管理）

最近のインフラ構成では、アプリケーションは"N-tier"とう形ではなくなってきています。別の部品が追加され、スケールや末端ユーザの機能リクエストに合わせて付加的なサービスが必要になってきています。

既にサービスは始まっています。

待った！ 更に：

* メッセージキュー
* 検索システム
* 外部サービスへの対応（e.g., 課金、稼働状況監視、分析）

動向把握とモニターリングを忘れないように！


!SLIDE
# 構成が更に複雑化していくと

<center><img src="../images/complex-infrastructure.png" />
<img src="../images/third-party-services.png" /></center>


!SLIDE
# Chefの登場！

<center><img src="../images/oc-chef-logo.png" height="394" width="500" /></center>


!SLIDE
# Chefで問題を解決

Chef is designed to help manage this kind of complexity. You may have
met already!

* Configuration management tool
* Systems integration framework
* API for infrastructure management


!SLIDE
# Chef: ツールついて

Chef is a tool for configuration management.

* Declarative: What, not how
* Idempotent: Only take action if required
* Convergent: Takes care of itself

.notes Each of these topics is discussed in greater detail.


!SLIDE
# 宣言的なResource

You configure systems with Chef by writing self-documenting code. This
code is lists of *Resources* that configure the system to do its job.

Chef manages system resources with a declarative interface that
abstracts the details.

    @@@ruby
    package "bash" do
      action :install
    end

.notes This is the equivalent to the command `apt-get install bash` or
`yum install bash`.


!SLIDE
# 冪等的な動作

Chef Resources have *Providers* that take idempotent action to
configure the resource, but only if it needs to change.

    INFO: Processing package[apache2] action install (apache2::default line 20)
    DEBUG: package[apache2] checking package status for apache2
    DEBUG: package[apache2] current version is 2.2.20-1ubuntu1.1
    DEBUG: package[apache2] candidate version is 2.2.20-1ubuntu1.1
    DEBUG: package[apache2] is already installed - nothing to do

Chef providers handle the details of checking the current state
of the resource. Different platforms may have different providers for
managing the same type of resource, yum vs apt, init vs upstart.


!SLIDE
# 収束Node

Chef runs on the system, configuring the *Node*. The node is the
initial unit of authority about itself.

The node is responsible only for itself.

In Chef, a single run should completely configure the system. If it
does not, it is a bug (in your code, on the system, or in Chef
itself).

When Chef runs, it saves the node to the Chef Server, making that
information available through a network-accessible API.

We'll talk more about how Chef converges the node when we cover
Anatomy of a Chef run.

.notes Chef doesn't read minds, it tries to detect as much as it can
about the node.


!SLIDE
# Chef: フレームワークについて

Chef provides a framework for system integration.

* Resources are written in Chef Recipes, a Ruby domain-specific
  language (DSL).
* Recipe helpers such as `search` allow dynamic data usage.
* Chef provides a library of primitives that can be used for other
  purposes.

.notes Each of these topics is discussed in greater detail.


!SLIDE
# Recipe Ruby DSL

Ruby is a 3rd generation interpreted programming language. Ruby has
features that make it easy to create domain specific languages. This
lends itself quite nicely to configuration management.

In Chef, Ruby gets out of the way, but it is still there when you need
it.

Chef *Recipes* are a pure Ruby domain specific language. They are
collected in *Cookbooks* along with associated components like config
files or libraries.

.notes By "Gets out of the way", the DSL doesn't require intimate Ruby
knowledge.


!SLIDE
# Recipeのヘルパー

Chef provides a number of recipe helpers to obtain and manipulate data
to use in Resources.

*Search* is used to discover information like IP addresses about other
 systems.

Arbitrary data about the infrastructure can be stored in *Data Bags*
and accessed in recipes.

Because Chef uses Ruby, you can create your own helpers, too.


!SLIDE
# LibraryとPrimitives

Chef can be used as a library within other applications. It speaks
JSON and the server has a RESTful API accessed over HTTP(S).

Cookbooks can extend Chef with new libraries, including new resources
and helpers to interact with 3rd party services.

Chef's included tools have plugin systems you can use to extend them.


!SLIDE
# Chef: APIについて

The Chef Server provides a network accessible API to stored data.

* Information about configured nodes
* Configuration policy in Cookbooks
* Descriptions of what policy to apply


!SLIDE
# Nodeデータ

Chef gathers information about the node it is running on and saves
this data to the Chef Server.

Node data is generated as a JSON key/value structure.

The JSON data is indexed for search by the Chef Server.


!SLIDE
# 設定ポリシー

Policy about the nodes is written in recipes, which are stored in
*Cookbooks*.

Cookbooks are uploaded to the Chef Server and distributed to the nodes
that should be configured.

Cookbooks have versions and dependencies, both of which affect what
code gets executed on particular nodes.


!SLIDE
# ポリシーの適応

Tying it all together are `roles` which are descriptions of the nodes.

A `webserver` role contains the list of cookbooks and node-specific
information required to fulfill serving HTTP traffic.

`webserver`のroleは、

nodeは、roleとrecipieのリストを持っています。chefはこれらのリストを基にnodeが正しく機能するように設定します。chefは、必要なモノのみをchef severよりダウンロードしてきます。


!SLIDE
# Chef まとめ: Configuration Management

* 設定のポリシーをresourceで宣言
* recipeにresourceを収集
* recipeと付随コードをcookbiookにパッケージ化
* role指定によって、cookbookの適応
* chefを実行し、roleに合わせてnodeを設定


!SLIDE
# Chef まとめ: Systems Integration

* 検索による、情報の収集
* 第３世代のプログラミング言語
* toolboxとprimitivesの動作を完全記述可
* 一回の実行で単システムを完全設定


!SLIDE
# 質問

* configuration managementとは何ですか？
* system integrationとは何ですか?
* declarative resourcesとは何ですか?
* chef resourceはどのように冪等性を担保していますか?
* recipesはどの言語で書かれていますか?
* recipesはどのようにしてnodeに配布されますか？
* 受講生の質問？