---
title: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
description: ヘッドレスアダプティブフォーム用の Visual Studio Code 拡張機能
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス、アダプティブフォーム、Visual Studio Code 拡張機能
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 1%

---

# ヘッドレスアダプティブフォーム用のMicrosoft Visual Studio Code 拡張機能

Microsoft® Visual Studio Code を IDE として使用する場合は、Microsoft Visual Studio Code 用の Adaptive Forms拡張機能を使用できます。 この拡張には、次の機能があります。

* Visual Studio Code にアダプティブForms用の IntelliSense 機能を追加しました
* ヘッドレスアダプティブフォームコンポーネントの JSON 構文の検証とオートコンプリートに役立ちます。
* ヘッドレスアダプティブフォームの構造を簡単にナビゲートするパネルを提供します
* ヘッドレスアダプティブフォームの翻訳に役立ちます

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 前提条件

* ダウンロードとインストール [Microsoft Visual Studio Code 1.62.0以降](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). 古いバージョンがある場合、またはバージョンがインストールされていない場合は、最新バージョンをからダウンロードしてください。 [Microsoft Web サイト](https://code.visualstudio.com/docs/setup/setup-overview). Apple macOSのコマンドラインから Visual Studio を使用するには、 [コマンドラインからの起動](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* をダウンロードします。 [アダプティブフォームビルダー拡張機能](/help/assets/adaptive-form-builder-0.12.0.vsix).

## 拡張機能のインストール

1. コマンドプロンプトを開き、ダウンロードした拡張機能ファイルが格納されているディレクトリに移動します。 *adaptive-form-builder-[version].vsix*.

1. 次のコマンドを実行して、拡張機能をインストールします。

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![拡張機能のインストール](/help/assets/install-extension.png)


   .vsix ファイルについて詳しくは、 [Microsoft Visual Studio コードヘルプ](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix).
