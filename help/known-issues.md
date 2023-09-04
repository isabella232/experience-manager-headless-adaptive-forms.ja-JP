---
title: ヘッドレスアダプティブフォームの既知の問題
description: ヘッドレスアダプティブフォームの既知の問題
keywords: ヘッドレス, アダプティブフォーム, 既知の問題
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: ht
source-wordcount: '102'
ht-degree: 100%

---


# 既知の問題 {#known-issues}

* 編集、表示およびデータパターンがサポートされていない。（CQ-4327047）
* minItems 制約を動的に変更できない。（CQ-4342499）
* パネルレベルの検証に違反した場合でもエラーが発生しない。（CQ-4342373）
* ファイル検証に違反した場合でもエラーが発生しない。（CQ-4342372）
* カスタムプロパティが動的でない。（CQ-4342376）
* 式を使用して変更イベントでファイルデータを動的に変更すると無限ループになる。（CQ-4342377）
* 添付ファイルがヘルプテキストをサポートしていない。（CQ-4342370）
* 必須のチェックボックスが選択されていない場合でも、送信時にエラーが表示されない。（CQ-4342371）
* 添付ファイルに aria-label が付加されない。（CQ-4341494）