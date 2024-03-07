---
title: AEM ヘッドレスアダプティブフォームの概要
description: AEM Forms ヘッドレスアダプティブフォームを使用すると、ヘッドレス CMS またはヘッドフル CMS、React アプリケーション、単一ページアプリケーション（SPA）、web アプリ、モバイルアプリ、Amazon Alexa、Google アシスタント、WhatsApp などの様々なプラットフォームに対応するフォームを迅速かつ効率的に作成できます。ヘッドレスアダプティブフォームを使用すると、フォーム作成プロセスを効率化して、様々なデバイスやプラットフォームでユーザーのデータを簡単に収集できるようになります。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: ヘッドレス CMS, アダプティブフォーム, ヘッドレス UI, ヘッドフル CMS, 音声アシスタント, Alexa, チャットボット, WhatsApp アーキテクチャ
hide: true
hidefromtoc: true
exl-id: f6a383ea-684b-479d-a15f-8ebced75635e
source-git-commit: 1f70e2bb0e5f12e8ee5d948ef1d3cd2935f2274f
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 100%

---

# はじめに

Adobe Experience Manager（AEM）ヘッドレスアダプティブフォームは、Adobe Experience Manager プラットフォーム内でヘッドレス web フォームを作成および管理するためのソリューションです。この機能により、組織は、従来のグラフィカルユーザーインターフェイスの代わりに API を使用してアクセスおよび操作できるインタラクティブフォームを作成、公開および管理できるようになります。AEM ヘッドレスアダプティブフォームを使用すると、フォームの開発とデプロイメントにおける柔軟性とスケーラビリティが高まると共に、フォームのデザインと機能を特定のニーズに合わせてカスタマイズできるので、ユーザーエクスペリエンスを向上させることができます。このソリューションでは、AEM とヘッドレステクノロジーの機能を活用して、様々なユースケースやアプリケーションに合わせて web フォームを作成、管理およびデプロイできる堅牢なプラットフォームを提供します。

![任意の web サイト、アプリケーションまたは非視覚的なインタラクション内にフォームを作成し、ネイティブにレンダリングする](/help/assets/headless-forms-for-any-device.jpeg)

ヘッドレスアダプティブフォームは以下の場合に役立ちます。

* 高品質のマルチチャネルフォームを好みのプログラミング言語で作成
* デスクトップおよびモバイルアプリ、web サイト、チャットアプリケーションにフォームをネイティブに統合
* フォームアプリケーションで独自の UI コンポーネントを再利用
* [Adobe Experience Manager Forms の機能](https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html?lang=ja)を活用

さらに、任意の UI フレームワークとプログラミング言語を使用して、フォームをレンダリングする独自のコンポーネントを自由に開発できます。すぐに利用可能な React コンポーネントを使用して、ヘッドレスアダプティブフォームをレンダリングすることもできます。

<!-- 

## Key Features

<table style="width:100%;">
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Responsive Forms</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Communication API</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Integrate RDBMS, OData, Or Microsoft SOAP services, as well as protocols like Swagger 2.0 to connect to just about anything.</p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Save and resume forms</h2>
          <p>Allow clients to save in-progress forms and return later to complete them, even on another device.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
      <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Form analytics and reporting</h2>
          <p>Out-of-the-box, customizable dashboards make it easy to apply analytics to forms to gain insight for actionable areas of improvement.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Route application submissions through customized workflows and a centralized dashboard for review, approval, and digital signatures by back-office employees — even when employees are on the go on a mobile device.
          </p>
        </div>
      </div>
    </td>
  </tr>
</table>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
        <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/04-overview-search.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="画像 1" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">見出し 1</h2>
        <p>説明 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="画像 2" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">見出し 2</h2>
        <p>説明 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="画像 3" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">見出し 3</h2>
        <p>説明 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>

-->

## ヘッドレスアダプティブフォームを使用できるユーザー {#who-can-use-headless-adaptive-forms}

最新の JavaScript フレームワークに精通しているすべてのフロントエンド開発者が、ヘッドレスアダプティブフォームを使用できます。開発者は、React などのフロントエンド言語に関する既存の専門知識を活用して、エンタープライズクラスの優れたデータキャプチャエクスペリエンスを作成できます。

ヘッドレスアダプティブフォームを開発するために、Adobe Experience Manager の事前知識は必要ありません。

<!-- 
## How to join the early adopter program? {#how-to-join-early-adopter-forms}

The service is available for AEM Forms as a Cloud Service and AEM 6.5.16.0 Forms or later On-Premise term customers and Adobe-Managed Service enterprise customers. Send an email to [headlessadaptiveforms@adobe.com](mailto:headlessadaptiveforms@adobe.com) from your official email ID to join the early adopter program. 

-->
