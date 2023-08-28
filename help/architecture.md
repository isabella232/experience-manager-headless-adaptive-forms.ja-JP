---
title: ヘッドレスアダプティブフォームのアーキテクチャ
description: AEM FormsヘッドレスアダプティブFormsのアーキテクチャと、様々なプラットフォーム向けのフォームをすばやく作成する方法について説明します。 この記事では、ヘッドレスアダプティブFormsの動作方法と、異なるアプリケーションと統合してフォームの作成プロセスを簡略化する方法に関するインサイトを提供します。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス，アダプティブフォーム，アーキテクチャ
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# ヘッドレスアダプティブフォームの仕組み

ヘッドレスアダプティブフォームは、基本的に、フォームフィールド（テキストボックス、選択肢、その他多くのフィールド）と対応するルール（条件付きロジック）で構成される JSON 構造（スキーマ）で、インタラクティブな動作をフォームに追加します。 アプリケーションまたは Web サイトで REST API を使用して、ホストされる JSON 構造を要求し、その JSON 構造をアプリまたは Web サイト内のフォームとしてネイティブにレンダリングできます。 1 つのヘッドレスアダプティブフォームは、アプリや Web サイトに特有の変更を加えることなく、複数の Web ページやアプリケーションに対応できます。

![ヘッドレスアダプティブフォームの仕組み](/help/assets/how-headless-adaprive-forms-work.png)

## アーキテクチャ {#architecture}

一般的なヘッドレスアダプティブフォームアーキテクチャは、Adobe Experience Manager Forms Server、Adobe Experience Manager Forms Server でホストされるヘッドレスアダプティブフォーム、およびチャネル固有のフォームレンディションのフロントエンドアプリ（Web サイト、モバイルアプリケーション、JavaScript アプリ、チャットアプリなど）で構成されます。

ヘッドレスアダプティブフォームデプロイメントの一般的なアーキテクチャは、次のようになります。

![アーキテクチャ](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### ヘッドレスアダプティブフォームの実装のコンポーネント

**Adobe Experience Manager Server**:Adobe Experience Managerは、ヘッドレスアダプティブフォームのホストとして機能すると共に、次のバックエンド機能を提供します。

* ヘッドレスフォームの送信ステータスのリスト、取得、事前入力、検証、送信、追跡を行う RESTful API です。
* ヘッドレスアダプティブフォームを簡単に開発するためのビジュアルエディター。
* Forms Data Model を使用して、異なるデータソースに対してデータを受け取るか送信します。
* 複雑なタスクを自動化するワークフローエンジン。

**ヘッドレスアダプティブフォーム**：ヘッドレスアダプティブフォームは、.json ファイルとして表されます。 JSON 構造は、フォームのコンポーネント、制約、構造を定義します。

**フロントエンドアプリ**:SPA（シングルページアプリケーション）、モバイルアプリ、JavaScript アプリなどのフロントエンドアプリで、ヘッドレスアダプティブフォーム（JSON フォーム表現）を使用して、クライアントでフォームをレンダリングします。 ヘッドレスアダプティブフォームに付属の React レンダラーコンポーネントを使用して、アダプティブフォームをレンダリングしたり、独自のカスタムコンポーネントを作成してヘッドレスアダプティブフォームをネイティブにレンダリングしたりできます。

<!-- ### Understanding Headless adaptive forms definition -->



### 開発者ツール

一般的な開発サイクルでは、まずAdobe Experience Manager Forms Server 上でヘッドレスアダプティブフォームを作成し、ホストします。 2 つ目の手順では、UI コンポーネントをマッピングするか、Google Material UI や Chakra UI などのパブリック UI コンポーネントライブラリを使用してフォームのスタイルを設定します。 最後の手順では、アプリケーション（Web サイト、モバイルアプリケーション、JavaScript アプリ、チャットアプリケーション、その他多くのサーフェス）でヘッドレスアダプティブフォームを取得して表示します。

以下のツールを使用して、ヘッドレスアダプティブフォームを作成し、アプリケーションに統合することができます。

**Forms Web SDK（クライアント側ランタイム）**:Forms Web SDK は、クライアント側の JavaScript ライブラリです。 これにより、フォームフィールドにクライアント側の検証を適用し、フォームの状態を維持し、UI レイヤーまたはアダプティブフォームのレンダリングされたコンポーネントにフォームを接続するためのフックを提供できます。 これにより、ユーザーはフォームの様々なフィールドに適用された制限と、フォームの JSON 構造を UI フレームワークに接続するためのフックを検証できます。 Forms Web SDK には、次のコンポーネントがあります。

* **ビジネスルールプロセッサ**：ビジネスルールプロセッサーは、フォームの JSON 構造を入力として受け入れ、フォームフィールドの状態を管理し、ルールを実行し、JSON に存在するイベントハンドラーを管理します。
* **React バインダー**：フォームコンポーネントに状態を追加するためのフックをコントローラー上に提供します。 また、フォームの事前入力にも役立ちます。
* **コンポーネントライブラリ**:React Spectrum コンポーネントを提供し、React Binder モジュールのフックを使用して、これらのコンポーネントに状態を追加します。

Forms Web SDK は、フォームの様々なフィールドに適用された制約を検証する API を提供するだけでなく、ヘッドレスアダプティブフォームを UI フレームワークに接続するためのフックを提供します。 また、ヘッドレスアダプティブフォームをアプリケーションに統合する際に役立つヘッドレスアダプティブフォーム用の React レンダラも提供されま&#x200B;す。 Web SDK の次のコンポーネントを使用できます。

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

これらのコンポーネントはすべてAEMアーキタイプに含まれています。 ヘッドレスアダプティブフォーム用のAEM Archetype 37 以降のプロジェクトを作成する場合、上記のリストに記載されているライブラリの最新バージョンがプロジェクトに含まれます。

**開始済みのアプリ**:Adobeでは、ヘッドレスアダプティブフォームをすばやく使い始めるのに役立つ、開始済みのアプリケーションもリリースされています。

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) では、ヘッドレスアダプティブフォームの様々なコンポーネントの概要を説明しています。 また、サポートされるすべてのコンポーネント、対応するプロパティ、制約のリストも表示されます。

**Visual Studio Code 拡張機能**: [Visual Studio Code 拡張機能](visual-studio-code-extension-for-headless-adaptive-forms.md) 有効な JSON 構造を作成するのに役立ちます。 フォームの JSON 構造に対する IntelliSense のサポートと検証を提供し、JSON 構造のコンポーネントの追加、削除、名前変更などの共通の機能を提供します。

**アダプティブFormsバージョン 2.0 の仕様**：アダプティブFormsバージョン 2.0 の仕様では、ヘッドレスアダプティブフォームを定義する際に使用できるすべてのコンポーネント、制約、メソッドに関する詳細情報を提供します。 仕様は、 [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 形式を使用します。

**HTTP および JavaScript API**: [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) ヘッドレスフォームの送信ステータスのリスト、取得、検証、送信、追跡を行うことができます。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) は、ヘッドレスアダプティブフォームを JavaScript ベースの UI フレームワークと共に使用する際に役立ちます。

**JSON 式**:JSON 構造を照会し、ヘッドレスアダプティブフォームのルールを作成するのに役立つ、フォーム式の文法を実装しています。 この文法は、スプレッドシートに似た関数と演算子、および [JMESPath](https://jmespath.org/) JSON クエリ言語。 以下を使用すると、 [遊び場](https://opensource.adobe.com/json-formula/dist/index.html) を参照してください。