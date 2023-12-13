---
title: ヘッドレスアダプティブフォームのトラブルシューティング
description: ヘッドレスアダプティブフォームのトラブルシューティング
keywords: ヘッドレス, アダプティブフォーム, トラブルシューティング
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# トラブルシューティング

## アーキタイププロジェクトをローカル開発環境にデプロイできない

### 問題

`mvn -PautoInstallPackage clean install` または同様のコマンドを使用して AEM アーキタイププロジェクトをデプロイしようとすると、プロジェクトのデプロイに失敗します。

### 理由

この問題が発生する原因としては、node.js または NPM がサポートされていないバージョンであるか、インストールが破損していることが考えられます。

### 解決策

1. [現在インストールされている Node.js](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) を環境から完全に削除します。

1. Node.js 16.13.0 以降を NPM と共にインストールします。

1. コンピューターを再起動します。


## `mvn clean install` コマンドの実行に失敗する

### 問題

`mvn clean install` または同様のコマンドを使用して AEM アーキタイププロジェクトをデプロイしようとすると、コマンドの実行に失敗します。

### 理由

この問題は、Git がインストールされていない場合に発生する可能性があります。

### 解決策

[Git の最新リリース](https://git-scm.com/downloads)をダウンロードしてインストールします。Git を初めて使用する場合は、[Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) を参照してください。
