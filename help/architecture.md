---
title: ヘッドレスアダプティブフォームのアーキテクチャ
description: AEM Forms ヘッドレスアダプティブフォームのアーキテクチャと、様々なプラットフォーム向けのフォームを迅速に作成するうえでこのアーキテクチャがどう役に立つかを説明します。この記事では、ヘッドレスアダプティブフォームの仕組みと、ヘッドレスアダプティブフォームを様々なアプリケーションと統合してフォーム作成プロセスを簡素化する方法について説明します。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, アーキテクチャ
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: ht
source-wordcount: '916'
ht-degree: 100%

---


# ヘッドレスアダプティブフォームの仕組み

ヘッドレスアダプティブフォームは基本的に、フォームフィールド（テキストボックス、選択肢などの多くのフィールド）と、フォームにインタラクティブな動作を追加するための対応するルール（条件付きロジック）で構成される JSON 構造（スキーマ）です。アプリケーションや web サイトで REST API を使用して、ホストされた JSON 構造をリクエストし、その JSON 構造をアプリまたは web サイトのフォームとしてネイティブにレンダリングできます。1 つのヘッドレスアダプティブフォームで複数の web ページやアプリケーションに対応でき、アプリや web サイトに合わせて変更を加える必要はありません。

![ヘッドレスアダプティブフォームの仕組み](/help/assets/how-headless-adaprive-forms-work.png)

## アーキテクチャ {#architecture}

典型的なヘッドレスアダプティブフォームアーキテクチャは、Adobe Experience Manager Forms Server、Adobe Experience Manager Forms サーバーでホストされるヘッドレスアダプティブフォーム、チャネル固有のフォームレンディションに対応するフロントエンドアプリ（web サイト、モバイルアプリケーション、JavaScript アプリ、チャットアプリなど）で構成されます。

ヘッドレスアダプティブフォームデプロイメントの典型的なアーキテクチャは次のようになります。

![アーキテクチャ](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### ヘッドレスアダプティブフォーム実装のコンポーネント

**Adobe Experience Manager Server**：Adobe Experience Manager は、ヘッドレスアダプティブフォームのホストとして機能するだけでなく、次のバックエンド機能も提供します。

* ヘッドレスフォームの一覧、取得、事前入力、検証、送信、送信ステータスの追跡を行う RESTful API。
* ヘッドレスアダプティブフォームを簡単に開発できるビジュアルエディター。
* 様々な種類のデータソースにデータを送受信するためのフォームデータモデル。
* 複雑なタスクを自動化するワークフローエンジン。

**ヘッドレスアダプティブフォーム**：ヘッドレスアダプティブフォームは .json ファイルで表されます。JSON 構造は、フォームのコンポーネント、制約および構造を定義します。

**フロントエンドアプリ**：SPA（単一ページアプリケーション）、モバイルアプリ、JavaScript アプリなどのフロントエンドアプリは、クライアントでヘッドレスアダプティブフォーム（JSON 表現のフォーム）を使用しフォームをレンダリングします。ヘッドレスアダプティブフォームに付属の React レンダラーコンポーネントを使用すると、アダプティブフォームをレンダリングしたり、独自のカスタムコンポーネントを作成してヘッドレスアダプティブフォームをネイティブにレンダリングしたりできます。

<!-- ### Understanding Headless adaptive forms definition -->



### 開発者ツール

一般的な開発サイクルでは、まず Adobe Experience Manager Forms サーバー上でヘッドレスアダプティブフォームを作成しホストします。次に、UI コンポーネントをマッピングするか、Google マテリアル UI や Chakra UI などの公開 UI コンポーネントライブラリを使用してフォームのスタイルを設定します。最後に、アプリケーション（web サイト、モバイルアプリケーション、JavaScript アプリケーション、チャットアプリケーションなどの様々なサーフェス）でヘッドレスアダプティブフォームを取得し表示します。

ヘッドレスアダプティブフォームを作成してアプリケーションに統合するには、次のツールが役立ちます。

**Forms Web SDK（クライアントサイドランタイム）**：Forms Web SDK は、クライアントサイドの JavaScript ライブラリです。Forms Web SDK は、フォームフィールドにクライアントサイドの検証を適用したり、フォームの状態を維持したりするために使用できるだけでなく、UI レイヤーまたはアダプティブフォームのレンダリングされたコンポーネントにフォームを接続するためのフックとしても機能します。ユーザーは Forms Web SDK をフォームの様々なフィールドに適用された制約の検証に使用したり、フォームの JSON 構造を UI フレームワークに接続するためのフックとして使用したりできます。Forms Web SDK には次のコンポーネントがあります。

* **ビジネスルールプロセッサー**：ビジネスルールプロセッサーはフォームの JSON 構造を入力として受け取り、フォームフィールドの状態を管理し、ルールを実行し、JSON に存在するイベントハンドラーを実行します。
* **React Binder**：フォームコンポーネントにステートを追加するためのフックをコントローラーに提供します。また、フォームの事前入力にも役立ちます。
* **コンポーネントライブラリ**：React Spectrum コンポーネントを提供し、React Binder モジュールのフックを使用して対象のコンポーネントにステートを追加します。

Forms Web SDK は、フォームの様々なフィールドに適用された制約を検証する API を提供するだけでなく、ヘッドレスアダプティブフォームを UI フレームワークに接続するためのフックとしても機能します。また、アプリケーションへのヘッドレスアダプティブフォームの統合に役立つ、ヘッドレスアダプティブフォーム用の React Renderer も提供します。Web SDK の次のコンポーネントが利用可能です。

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

これらのコンポーネントはすべて AEM アーキタイプに含まれています。ヘッドレスアダプティブフォーム用に AEM Archetype 37 以降のプロジェクトを作成する場合は、上記のライブラリの最新バージョンがプロジェクトに含まれます。

**起動済みのアプリケーション**：ヘッドレスアダプティブフォームの使用をすぐに開始するのに役立つ、起動済みのアプリケーションもリリースされています。

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**ストーリーブック**：[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)は、ヘッドレスアダプティブフォームの様々なコンポーネントの概要を示します。また、サポートされているすべてのコンポーネント、対応するプロパティおよび制約のリストも提供します。

**Visual Studio Code 拡張機能**：[Visual Studio Code 拡張機能](visual-studio-code-extension-for-headless-adaptive-forms.md)は、有効な JSON 構造を作成するのに役立ちます。これは、JSON 構造のコンポーネントの追加、削除、名前変更などの一般的な機能に加えて、IntelliSense のサポートやフォームの JSON 構造の検証も提供します。

**アダプティブフォームバージョン 2.0 の仕様**：アダプティブフォームバージョン 2.0 の仕様には、ヘッドレスアダプティブフォームの定義に使用できるすべてのコンポーネント、制約およびメソッドに関する詳細情報が記載されています。仕様は [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 形式で入手可能です。

**HTTP と JavaScript API**：[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) を使用すると、ヘッドレスフォームの一覧、取得、検証、送信、送信ステータスの追跡を行うことができます。[JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) は、JavaScript ベースの UI フレームワークでヘッドレスアダプティブフォームを使用するのに役立ちます。

**JSON 式**：JSON 構造をクエリし、ヘッドレスアダプティブフォームのルールを作成するのに役立つ、フォーム式の文法を実装したものです。この文法は、スプレッドシートに似た関数と演算子および JSON クエリ言語である [JMESPath](https://jmespath.org/) をマッシュアップしたものです。[プレイグラウンド](https://opensource.adobe.com/json-formula/dist/index.html)を使用して、JSON 式の構文と機能を調べることができます。