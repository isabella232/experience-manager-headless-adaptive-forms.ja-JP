---
title: よくある質問
description: よくある質問
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス, アダプティブフォーム, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: ht
source-wordcount: '423'
ht-degree: 100%

---

# よくある質問（FAQ） {#headless-adaptive-forms-faq}

## ヘッドレスアダプティブフォームを使用するには React.js の知識が必要ですか？

任意のフレームワーク、ライブラリまたは言語を使用してヘッドレスアダプティブフォームをレンダリングし、REST API を使用してフォームを検証および送信できます。標準提供の AF コアライブラリは、フレームワークに依存しません。標準提供の React Render および React コンポーネントライブラリは、参考までに提供されています。独自のコンポーネントを開発でき、これらのライブラリには限定されません。

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## ヘッドレスアダプティブフォームを使用するには、Forms as a Cloud Service サンドボックスが必要ですか？

スターターアプリを使用して、ヘッドレスアダプティブフォームの開発とスタイル設定を開始できます。バックエンドのフォーム機能とともにヘッドレスアダプティブフォームをホストし提供するには、Forms as a Cloud Service が必要です。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## ヘッドレスアダプティブフォームのプレビューはどこで入手できますか？ {#storybook-example}

スターターアプリを使用して、カスタムのヘッドレスアダプティブフォームをレンダリングしプレビューできます。[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)の例を変更して、ヘッドレスアダプティブフォームをプレビューすることもできます。

![](/help/assets/storybook-example.png)

## カスタムフレームワークでヘッドレスアダプティブフォームを使用することはできますか？

ヘッドレスアダプティブフォームは[標準仕様](/help/assets/Headless-Adaptive-Form-Specification.pdf)に基づいています。仕様を拡張して、カスタムコンポーネントの構築に使用できます。例えば、Chakra UI、Vue.js などのコンポーネントです。

## ヘッドレスアダプティブフォームはカスケードフィールドをサポートしていますか？

カスケードフィールドでは、2 番目のフィールドの内容は、最初のフィールドで選択された内容に依存します。カスケードフィールドの例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&amp;args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)に含まれています。

## ヘッドレスアダプティブフォームでは、パーソナライズされたデータをフォームに事前入力できますか？

ヘッドレスアダプティブフォームを使用すると、パーソナライズされたデータをフォームに事前入力できます。ヘッドレスアダプティブフォームに事前入力する方法の例が[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)に含まれています。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Angular SPA でヘッドレスアダプティブフォームを使用できますか？

Web SDK を使用して、ヘッドレスアダプティブフォームを Angular SPA と統合できます。どのようなフレームワークにも依存しません。React SDK を参照用に使用できます。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## ヘッドレス AF を開発しやすくなるプラグインはありますか？

はい、Microsoft Visual Studio Code の拡張機能を利用できます。ヘッドレスアダプティブフォーム JSON を手動で作成する便利な方法が用意されています。

## ヘッドレスアダプティブフォームを CRM に接続してデータを読み書きできますか？

Microsoft Dynamics や Salesforce を使用して、ヘッドレスアダプティブフォームを送信または事前入力できます。CRM とは別に、ヘッドレスアダプティブフォームでは、REST エンドポイント、メールおよびカスタム送信アクションを使用した送信または事前入力をサポートしています。
