TERASOLUNA Global Frameworkのスタック
================================================================================

.. only:: html

 .. contents:: 目次
    :depth: 3
    :local:

TERASOLUNA Global FrameworkのSoftware Framework概要
--------------------------------------------------------------------------------

TERASOLUNA Global Frameworkで使用するSoftware Frameworkは独自のフレームワークではなく、\ `Spring Framework <http://projects.spring.io/spring-framework/>`_\ を中心としたOSSの組み合わせである。

.. figure:: images/introduction-software-framework.png
   :width: 95%


Software Frameworkの主な構成要素
--------------------------------------------------------------------------------

TERASOLUNA Global Frameworkを構成するライブラリを以下に示す。

.. figure:: images/introduction-software-stack.png
   :width: 95%

DIコンテナ
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
DIコンテナとしてSpring Frameworkを利用する。


* `Spring Framework 4.1 <http://docs.spring.io/spring/docs/4.1.3.RELEASE/spring-framework-reference/html/beans.html>`_

MVCフレームワーク
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Web MVCフレームワークとしてSpring MVCを利用する。

* `Spring MVC 4.1 <http://docs.spring.io/spring/docs/4.1.3.RELEASE/spring-framework-reference/html/mvc.html>`_

O/R Mapper
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

本ガイドラインでは、以下の\ **いずれか**\ を想定している。

* `JPA2.1 <http://download.oracle.com/otn-pub/jcp/persistence-2_1-fr-eval-spec/JavaPersistence.pdf>`_

  * プロバイダは、\ `Hibernate 4.3 <http://docs.jboss.org/hibernate/orm/4.3/manual/en-US/html_single/>`_\ を使用する。

* `MyBatis 3.2 <http://mybatis.github.io/mybatis-3/>`_

  * Spring Frameworkとの連携ライブラリとして、\ `MyBatis-Spring <http://mybatis.github.io/spring/>`_\ を使用する。

* `MyBatis 2.3.5 <https://mybatis.googlecode.com/files/MyBatis-SqlMaps-2_en.pdf>`_

  * ラッパーとして、\ `TERASOLUNA Framework <http://sourceforge.jp/projects/terasoluna/releases/?package_id=6896>`_\ のDAO(TERASOLUNA DAO)を使用する。

.. note::

  MyBatisは正確には「SQL Mapper」であるが、本ガイドラインでは「O/R Mapper」に分類する。

.. warning::

  どんなプロジェクトでもJPAを採用できるわけではない。"テーブルがほとんど正規化されいない"、"テーブルのカラム数が多すぎる"というテーブル設計がされている場合に、JPAの利用は難しい。

  また、本ガイドラインではJPAの基本的な説明は行っておらず、JPA利用経験者がチーム内にいることが前提である。

View
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
ViewにはJSPを利用する。

JSPをTiles化する場合は、

* `Apache Tiles 3.0 <http://tiles.apache.org/framework/index.html>`_

を利用する。

セキュリティ
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
認証・認可のフレームワークとしてSpring Securityを利用する。

* `Spring Security 3.2 <http://projects.spring.io/spring-security/>`_

.. tip::

    Spring Security 3.2 から、認証・認可の仕組みの提供に加えて、
    悪意のある攻撃者からWebアプリケーションを守るための仕組みが強化されている。

    悪意のある攻撃者からWebアプリケーションを守るための仕組みについては、

    * :doc:`../Security/CSRF`
    * :ref:`SpringSecurityAppendixSecHeaders`

    を参照されたい。

バリデーション
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* 単項目チェックには\ `BeanValidation 1.1 <http://download.oracle.com/otn-pub/jcp/bean_validation-1_1-fr-eval-spec/bean-validation-specification.pdf>`_\ を利用する。

  * 実装は、\ `Hibernate Validator 5.1 <http://docs.jboss.org/hibernate/validator/5.1/reference/en-US/html/>`_\ を利用する。

* 相関チェックには\ `Bean Validation <http://download.oracle.com/otn-pub/jcp/bean_validation-1_1-fr-eval-spec/bean-validation-specification.pdf>`_\ 、もしくは\ `Spring Validation <http://docs.spring.io/spring/docs/4.1.3.RELEASE/spring-framework-reference/html/validation.html#validator>`_\ を利用する。

  * 使い分けについては\ :doc:`../ArchitectureInDetail/Validation`\ を参照されたい。



ロギング
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* ロガーのAPIは\ `SLF4J <http://www.slf4j.org>`_\ を使用する。

  * ロガーの実装は、\ `Logback <http://logback.qos.ch/>`_\ を利用する。


共通ライブラリ
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* \ `https://github.com/terasolunaorg/terasoluna-gfw <https://github.com/terasolunaorg/terasoluna-gfw>`_\
* 詳細は\ :ref:`frameworkstack_common_library`\ を参照されたい。

利用するOSSのバージョン
--------------------------------------------------------------------------------

version 1.1.0.RELEASEで利用するOSSの一覧を以下に示す。

.. tip::

    version 1.1.0.RELEASEより、
    `Spring IO platform <http://platform.spring.io/platform/>`_\ を親プロジェクトに指定する構成を採用している。

    Spring IO platformを親プロジェクトに指定することで、

    * Spring Frameworkが提供しているライブラリ
    * Spring Frameworkが依存しているOSSライブラリ
    * Spring Frameworkと相性のよいOSSライブラリ

    への依存関係を解決しており、
    TERASOLUNA Global Frameworkで使用するOSSのバージョンは、原則として、Spring IO platformの定義に準じている。

    なお、version 1.1.0.RELEASEで指定しているSpring IO platformのバージョンは、`1.1.0.RELEASE <http://docs.spring.io/platform/docs/1.1.0.RELEASE/reference/htmlsingle/>`_\ である。

.. tabularcolumns:: |p{0.15\linewidth}|p{0.25\linewidth}|p{0.25\linewidth}|p{0.25\linewidth}|p{0.05\linewidth}|p{0.05\linewidth}|
.. list-table::
    :header-rows: 1
    :stub-columns: 1
    :widths: 15 25 25 25 5 5

    * - Type
      - GroupId
      - ArtifactId
      - Version
      - Spring IO platform
      - Remarks
    * - Spring
      - org.springframework
      - spring-aop
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-aspects
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-beans
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-context
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-context-support
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-core
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-expression
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-jdbc
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-orm
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-tx
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-web
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework
      - spring-webmvc
      - 4.1.3.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.data
      - spring-data-commons
      - 1.9.1.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.security
      - spring-security-acl
      - 3.2.5.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.security
      - spring-security-config
      - 3.2.5.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.security
      - spring-security-core
      - 3.2.5.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.security
      - spring-security-taglibs
      - 3.2.5.RELEASE
      - \*
      -
    * - Spring
      - org.springframework.security
      - spring-security-web
      - 3.2.5.RELEASE
      - \*
      -
    * - JPA(Hibernate)
      - antlr
      - antlr
      - 2.7.7
      - \*
      - \*1
    * - JPA(Hibernate)
      - dom4j
      - dom4j
      - 1.6.1
      - \*
      - \*1
    * - JPA(Hibernate)
      - org.hibernate
      - hibernate-core
      - 4.3.7.Final
      - \*
      - \*1
    * - JPA(Hibernate)
      - org.hibernate
      - hibernate-entitymanager
      - 4.3.7.Final
      - \*
      - \*1
    * - JPA(Hibernate)
      - org.hibernate.common
      - hibernate-commons-annotations
      - 4.0.5.Final
      - \*
      - \*1 \*5
    * - JPA(Hibernate)
      - org.hibernate.javax.persistence
      - hibernate-jpa-2.1-api
      - 1.0.0.Final
      - \*
      - \*1 \*5
    * - JPA(Hibernate)
      - org.javassist
      - javassist
      - 3.18.1-GA
      - \*
      - \*1
    * - JPA(Hibernate)
      - org.jboss
      - jandex
      - 1.1.0.Final
      - \*
      - \*1 \*5
    * - JPA(Hibernate)
      - org.jboss.logging
      - jboss-logging-annotations
      - 1.2.0.Final
      - \*
      - \*1 \*5 \*6
    * - JPA(Hibernate)
      - org.jboss.spec.javax.transaction
      - jboss-transaction-api_1.2_spec
      - 1.0.0.Final
      - \*
      - \*1 \*5
    * - JPA(Hibernate)
      - org.springframework.data
      - spring-data-jpa
      - 1.7.1.RELEASE
      - \*
      - \*1
    * - MyBatis3
      - org.mybatis
      - mybatis
      - 3.2.8
      -
      - \*2
    * - MyBatis3
      - org.mybatis
      - mybatis-spring
      - 1.2.2
      -
      - \*2
    * - MyBatis2
      - jp.terasoluna.fw
      - terasoluna-dao
      - 2.0.5.0
      -
      - \*3
    * - MyBatis2
      - jp.terasoluna.fw
      - terasoluna-ibatis
      - 2.0.5.0
      -
      - \*3
    * - MyBatis2
      - org.mybatis
      - mybatis
      - 2.3.5
      -
      - \*3
    * - DI
      - javax.inject
      - javax.inject
      - 1
      - \*
      -
    * - AOP
      - aopalliance
      - aopalliance
      - 1
      - \*
      -
    * - AOP
      - org.aspectj
      - aspectjrt
      - 1.8.4
      - \*
      -
    * - AOP
      - org.aspectj
      - aspectjweaver
      - 1.8.4
      - \*
      -
    * - ログ出力
      - ch.qos.logback
      - logback-classic
      - 1.1.2
      - \*
      -
    * - ログ出力
      - ch.qos.logback
      - logback-core
      - 1.1.2
      - \*
      - \*5
    * - ログ出力
      - org.lazyluke
      - log4jdbc-remix
      - 0.2.7
      -
      -
    * - ログ出力
      - org.slf4j
      - jcl-over-slf4j
      - 1.7.7
      - \*
      -
    * - ログ出力
      - org.slf4j
      - slf4j-api
      - 1.7.7
      - \*
      -
    * - JSON
      - com.fasterxml.jackson.core
      - jackson-annotations
      - 2.4.4
      - \*
      -
    * - JSON
      - com.fasterxml.jackson.core
      - jackson-core
      - 2.4.4
      - \*
      -
    * - JSON
      - com.fasterxml.jackson.core
      - jackson-databind
      - 2.4.4
      - \*
      -
    * - JSON
      - com.fasterxml.jackson.datatype
      - jackson-datatype-joda
      - 2.4.4
      - \*
      -
    * - 入力チェック
      - javax.validation
      - validation-api
      - 1.1.0.Final
      - \*
      -
    * - 入力チェック
      - org.hibernate
      - hibernate-validator
      - 5.1.3.Final
      - \*
      -
    * - 入力チェック
      - org.jboss.logging
      - jboss-logging
      - 3.1.3.GA
      - \*
      - \*5
    * - 入力チェック
      - com.fasterxml
      - classmate
      - 1.0.0
      - \*
      - \*5
    * - Bean変換
      - commons-beanutils
      - commons-beanutils
      - 1.9.2
      - \*
      - \*4
    * - Bean変換
      - net.sf.dozer
      - dozer
      - 5.5.1
      -
      - \*4
    * - Bean変換
      - net.sf.dozer
      - dozer-spring
      - 5.5.1
      -
      - \*4
    * - Bean変換
      - org.apache.commons
      - commons-lang3
      - 3.3.2
      - \*
      - \*4
    * - 日付操作
      - joda-time
      - joda-time
      - 2.5
      - \*
      -
    * - 日付操作
      - joda-time
      - joda-time-jsptags
      - 1.1.1
      -
      - \*4
    * - 日付操作
      - org.jadira.usertype
      - usertype.core
      - 3.2.0.GA
      -
      - \*1
    * - 日付操作
      - org.jadira.usertype
      - usertype.spi
      - 3.2.0.GA
      -
      - \*1
    * - コネクションプール
      - org.apache.commons
      - commons-dbcp2
      - 2.0.1
      - \*
      - \*4
    * - コネクションプール
      - org.apache.commons
      - commons-pool2
      - 2.2
      - \*
      - \*4
    * - Tiles
      - commons-digester
      - commons-digester
      - 2.1
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-api
      - 3.0.5
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-core
      - 3.0.5
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-jsp
      - 3.0.5
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-servlet
      - 3.0.5
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-template
      - 3.0.5
      - \*
      - \*4 \*5
    * - Tiles
      - org.apache.tiles
      - tiles-autotag-core-runtime
      - 1.1.0
      - \*
      - \*4 \*5
    * - Tiles
      - org.apache.tiles
      - tiles-request-servlet
      - 1.0.6
      - \*
      - \*4 \*5
    * - Tiles
      - org.apache.tiles
      - tiles-request-api
      - 1.0.6
      - \*
      - \*4
    * - Tiles
      - org.apache.tiles
      - tiles-request-jsp
      - 1.0.6
      - \*
      - \*4 \*5
    * - ユーティリティ
      - com.google.guava
      - guava
      - 17.0
      - \*
      -
    * - ユーティリティ
      - commons-collections
      - commons-collections
      - 3.2.1
      - \*
      - \*4
    * - ユーティリティ
      - commons-io
      - commons-io
      - 2.4
      - \*
      - \*4
    * - サーブレット
      - javax.servlet
      - jstl
      - 1.2
      - \*
      -

#. | データアクセスに、JPAを使用する場合に依存するライブラリ
#. | データアクセスに、MyBatis3を使用する場合に依存するライブラリ
#. | データアクセスに、MyBatis2を使用する場合に依存するライブラリ
#. | 共通ライブラリに依存しないが、TERASOLUNA Global Frameworkでアプリケーションを開発する場合に、利用することを推奨しているライブラリ
#. | Spring IO platformでサポートしているライブラリが個別に依存しているライブラリ
   | (Spring IO platformとしては依存関係の管理は行っていないライブラリ)
#. | Spring IO platformで適用されるバージョンが、BetaやRC(Release Candidate)であるライブラリ
   | (TERASOLUNA Global Framework側でGAのバージョンを明示的に指定しているライブラリ)

.. _frameworkstack_common_library:


共通ライブラリの構成要素
--------------------------------------------------------------------------------

\ `共通ライブラリ <https://github.com/terasolunaorg/terasoluna-gfw>`_\ は、TERASOLUNA Global Frameworkが含むSpring Ecosystem や、その他依存ライブラリでは足りない+αな機能を提供するライブラリである。
基本的には、このライブラリがなくてもTERASOLUNA Global Frameworkによるアプリケーション開発は可能であるが、"あると便利"な存在である。

.. tabularcolumns:: |p{0.05\linewidth}|p{0.30\linewidth}|p{0.35\linewidth}|p{0.30\linewidth}|
.. list-table::
    :header-rows: 1
    :widths: 5 30 35 30

    * - 項番
      - プロジェクト名
      - 概要
      - Javaソースコード有無
    * - | (1)
      - | terasoluna-gfw-common
      - | Webに限らず、汎用的に使用できる機能
      - | 有
    * - | (2)
      - | terasoluna-gfw-web
      - | Webアプリケーションを作成する場合に使用する機能群
      - | 有
    * - | (3)
      - | terasoluna-gfw-jpa
      - | JPAを使用する場合の、依存関係定義
      - | 無
    * - | (4)
      - | terasoluna-gfw-mybatis3
      - | MyBatis3を使用する場合の、依存関係定義
      - | 無
    * - | (5)
      - | terasoluna-gfw-mybatis2
      - | MyBatis2を使用する場合の、依存関係定義
      - | 無
    * - | (6)
      - | terasoluna-gfw-security-core
      - | Spring Securityを使用する場合の、依存関係定義(Web以外)
      - | 無
    * - | (7)
      - | terasoluna-gfw-security-web
      - | Spring Securityを使用する場合の依存関係定義(Web関連)、およびSpring Securityの拡張
      - | 有

Javaソースコードを含まないものは、ライブラリの依存関係のみ定義しているプロジェクトである。



terasoluna-gfw-common
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* 共通例外機構

  * 例外クラス
  * 例外ロガー
  * 例外コード
  * 例外ログ出力インターセプタ

* システム日付
* コードリスト
* 処理結果メッセージ
* クエリー(SQL, JPQL)エスケープ
* シーケンサ


terasoluna-gfw-web
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* トランザクショントークン機構
* 共通例外ハンドラ
* コードリスト埋込インターセプタ
* 汎用ダウンロードView
* MDC情報ログ出力用サーブレットフィルタ群

  * 親サーブレットフィルタ
  * トラッキングIDログ出力用サーブレットフィルタ
  * MDCクリアサーブレットフィルタ

* EL関数群

  * XSS対策
  * URLエンコーディング
  * JavaBeansのクエリパラメータ展開

* ページネーション出力JSPタグ
* 結果メッセージ出力JSPタグ


terasoluna-gfw-security-web
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* 認証ユーザ名ログ出力用サーブレットフィルタ
* オープンリダイレクト脆弱性対策リダイレクトハンドラ

.. raw:: latex

   \newpage

