---
title: "[初心者向け]GoogleAnalytics を始める時に知っておいたほうが良いこと"
date: 2017-12-15T00:00:00+09:00
tags: ["ga", "Google Analytics"]
categories: ["川崎 卓満"]
---

## この記事について
[Google Analytics Advent Calendar 2017](https://qiita.com/advent-calendar/2017/ga) 16日目の記事です。
<br>
<br>
<br>

## はじめに
Google AnalyticsをサイトやWEBサービスで利用するにあたり、予め知っておいたほうが良いと思われる
心構えや、よく使われる内容について、軽く触れておきます。
<br>
<br>
<br>

## GAを使う前の心構え
### 1．gaで計測される割合に関する数値は、統計上支障がない程度に間引かれている
<p>
最近は多くのレポートが実数に基づいて作成されているようですが、一部のレポートでは

    このレポートは10万セッション数 （セッション数の 0.893%） に基づいています。

のような表示があります。
PVなどカウントを行うようなレポートは正確なカウントがされていますが、割合を表示するレポートの場合は、
一定のサンプル数で概算として出していることを予め認識し、事業側の方にも認識をしてもらいましょう。
</p>
<br>
<br>
<br>

### 2．一つのgaタグで計測できるのは、原則として一つのドメイン内です
デフォルトの使い方ですと、同一ドメイン内でしか計測できませんが、複数のドメインにまたがった行動の集計を取りたい場合は、クロスドメイントラッキングの設定が必要となります。<br>
B2Bでサービス提供している場合などで、顧客のサイトから提供しているサービスのサイトに画面がリンクしている等の場合は、クロスドメイントラッキングの設定が必要となってくると思います。
<br>
<br>
<br>

### 3．アクセスカウントの除外設定
開発者など自分たちのアクセスは、remote hostでのアクセスフィルタを利用して、カウントから除外するようにしたほうが良いです。<br>
公開直後は実は開発関係者が多く閲覧していたりして、PVなどに変に影響してしまう可能性があります。<br>
<br>
<br>
<br>

### 4．ga以外のアクセス解析用タグを利用したい場合
ga以外にも様々なマーケティング用タグがあるので、それらも一緒に埋め込みたい場合は、[google tag manager](https://tagmanager.google.com/) を利用すると良い
<br>
<br>
<br>

### 5．顧客へサイトの現状分析を行うために
直帰率、離脱率の違いを正しく認識し、顧客にも共通認識を持ってもらいましょう
<br>
<br>
#### 直帰率
- セッション的に最初に訪れたページでそのままセッション切れになった場合の、割合
- そのページを最初に見たタイミングのpv数に対して、そのぺーじだけ見てどこにも行かなかった割合
- そのサイトのトップページ、ランディングページに対して使用すると良いと思います

#### 離脱率
- 複数のページを遷移して最後に見ていたページの割合
- そのページの全pvから、そのページで離脱した数
- 何を持って離脱を判断してるの？
  - セッション管理されていて、デフォルトはページを見始めてから30分でセッションタイムアウトとなる
- ランディングページから、コンバージョンページすべてのページで利用されます。
- どのような画面遷移になるかによって、離脱されたくないページをベンチマークしておきましょう。

#### PV(PageView)数
- 純粋なページの閲覧回数

#### セッション数
- gaが定めているセッション単位での延べ接続数
  - 1セッション
    - 30分以内にページ遷移し続けている1クライアントの接続のこと
    - セッションの時間は変更することも可能

<br>
<br>
以上、これからGoogleAnalytics使おうと思っている方、ちょうど使い始めた方は
上記のことを意識しておくと事業側とも大きな認識の齟齬が起きにくくなるかと思います。
