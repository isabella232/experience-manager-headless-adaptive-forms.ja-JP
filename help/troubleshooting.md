---
title: ヘッドレスアダプティブFormsのトラブルシューティング
description: ヘッドレスアダプティブFormsのトラブルシューティング
keywords: ヘッドレス、アダプティブフォーム、トラブルシューティング
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 7%

---

# トラブルシューティング

## アーキタイププロジェクトをローカル開発環境にデプロイできません

### 問題

を使用する場合、 `mvn -PautoInstallPackage clean install` AEMアーキタイププロジェクトをデプロイするための同様のコマンドを使用すると、プロジェクトのデプロイに失敗します。

### 理由

この問題は、サポートされていないバージョンであるか、node.js または NPM のインストールが破損していることが原因で発生する可能性があります。

### 解決策

1. 完全に [Node.JS の現在のインストールを削除](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) を設定します。

1. Node.JS 16.13.0以降を NPM と共にインストールします。

1. コンピューターを再起動します。


## The `mvn clean install` コマンドが実行に失敗しました

### 問題

を使用する場合、 `mvn clean install` AEMアーキタイププロジェクトをデプロイするための同様のコマンドを実行すると、コマンドが実行に失敗します。

### 理由

Git がインストールされていない場合に発生する可能性があります。

### 解決策

をダウンロードしてインストールする [Git の最新リリース](https://git-scm.com/downloads). Git を初めて使用する場合は、 [Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
