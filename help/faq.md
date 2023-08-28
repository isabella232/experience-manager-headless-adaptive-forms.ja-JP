---
title: よくある質問
description: よくある質問
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス，アダプティブフォーム， FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 2%

---

# よくある質問（FAQ） {#headless-adaptive-forms-faq}

## ヘッドレスアダプティブフォームを使用する場合、React.js を知っておく必要はありますか？

任意のフレームワーク、ライブラリ、または言語を使用してヘッドレスアダプティブフォームをレンダリングし、アドビの REST API を使用してフォームを検証および送信することができます。 OOTB が提供する AF-core ライブラリは、フレームワークに依存しません。 OOTB が提供する React-Render ライブラリと React-component ライブラリは、ご利用の際に便利です。 独自のコンポーネントを開発することができ、これらのコンポーネントの使用に制限されません。

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## ヘッドレスアダプティブフォームを使用するには、Formsas a Cloud Serviceサンドボックスが必要ですか？

スターターアプリを使用して、ヘッドレスアダプティブフォームの開発とスタイル設定を開始できます。 ヘッドレスアダプティブフォームのホストと提供には、Formsがas a Cloud Service的に、バックエンドフォームの機能と共に必要です。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## ヘッドレスアダプティブフォームのプレビューはどこで入手できますか？ {#storybook-example}

スターターアプリを使用すると、カスタムのヘッドレスアダプティブフォームをレンダリングおよびプレビューできます。 また、 [ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) ヘッドレスアダプティブフォームのプレビュー例

![](/help/assets/storybook-example.png)

## カスタムフレームワークでヘッドレスアダプティブフォームを使用することは可能ですか？

ヘッドレスアダプティブフォームは、 [標準仕様](/help/assets/Headless-Adaptive-Form-Specification.pdf). 仕様を拡張して、カスタムコンポーネントを構築できます。 例えば、Chakra UI、Vue.js などのコンポーネントを使用できます。

## ヘッドレスアダプティブフォームはカスケードフィールドをサポートしていますか？

カスケードフィールドでは、2 番目のフィールドの内容は、最初のフィールドで選択した内容に応じて異なります。 The [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behavior—options&amp;args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].value:Choose+number+of+options;formJson.items[0].0].0]:1;formJsonitems[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) に、カスケードフィールドの例を示します。

## ヘッドレスアダプティブフォームでは、パーソナライズされたデータを使用したフォームの事前入力が可能ですか？

ヘッドレスアダプティブフォームを使用すると、パーソナライズされたデータをフォームに事前入力できます。 The [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) に、ヘッドレスアダプティブフォームの事前入力方法の例を示します。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## ヘッドレスアダプティブフォームをAngularSPAで使用することはできますか？

Web SDK を使用して、ヘッドレスアダプティブフォームを Web SPAとAngularで統合できます。 どのフレームワークとも独立しています。 React SDK を参照として使用できます。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## ヘッドレス AF の開発を容易にするプラグインはありますか？

はい、Microsoft Visual Studio Code で拡張機能を使用できます。 これにより、ヘッドレスアダプティブフォーム JSON を手動で作成する便利な方法が提供されます。

## ヘッドレスアダプティブフォームは、任意の CRM に接続して、データの読み取りや書き込みを行うことはできますか？

Microsoft Dynamics と Salesforce を使用して、ヘッドレスアダプティブフォームを送信したり、事前入力したりできます。 ヘッドレスアダプティブフォームは、CRM 以外にも、REST エンドポイント、電子メール、カスタム送信アクションを使用した送信または事前入力をサポートします。
