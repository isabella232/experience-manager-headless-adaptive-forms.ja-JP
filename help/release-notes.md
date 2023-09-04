---
title: AEM ヘッドレスアダプティブフォームの概要
description: AEM ヘッドレスアダプティブフォームの概要。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: ht
source-wordcount: '510'
ht-degree: 100%

---


# リリースノート

Experience Manager ヘッドレスアダプティブフォームの早期導入リリースへようこそ。リソースと手順に目を通して、このリリースの基本を理解し、リリースを最大限に活用してください。

Adobe Experience Manager ヘッドレスアダプティブフォームを使用すると、React や Angular などのフロントエンド UI フレームワークを使用してフォームアプリケーションを構築したり、状態管理、検証、他の様々なタッチポイントとの統合などの機能にアダプティブフォーム Web SDK を使用したりできます。

この早期導入リリースでは、[ローカル開発環境](setup-development-environment.md)でヘッドレスアダプティブフォームを使用できるようになります。ローカル開発環境を使用して、ヘッドレスアダプティブフォームを作成およびテストできます。

ヘッドレスアダプティブフォームは継続的に改善されています。最新の開発状況を確認するには、このページに定期的にアクセスしてください。このページでは、早期アクセス、最新リリース、新機能、改善、バグ修正、非推奨（廃止予定）の機能、特別な説明および将来の変更計画に関する情報を提供します。

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## 早期導入リリースで利用可能なアーティファクト

Adobe Experience Manager のヘッドレスアダプティブフォームを提供する過程で、次のアーティファクトが早期導入リリースで利用可能になります。

### AEM Forms as a Cloud Service SDK

AEM Forms as a Cloud Service SDK は、ヘッドレスアダプティブフォームの作成、保存および取得に役立ちます。また、ヘッドレスアダプティブフォームの事前入力、サーバーサイドのルール検証および送信サービスの提供にも役立ちます。

### Forms Web SDK

Forms Web SDK は、フォームの様々なフィールドに適用される制約を検証するための API と、フォームの JSON 構造を UI フレームワークに接続するためのフックを提供します。また、アプリケーションへのヘッドレスアダプティブフォームの統合に役立つ、ヘッドレスアダプティブフォーム用の React Renderer も提供します。Web SDK の次のコンポーネントが利用可能です。

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### ストーリーブック

[ストーリーブック](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)は、ヘッドレスアダプティブフォームの様々なコンポーネントの概要を示します。また、サポートされているすべてのコンポーネント、対応するプロパティおよび制約のリストも提供します。

### Forms コアコンポーネント

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

コアコンポーネントは、フォームの開発時間の短縮とメンテナンスコストの削減に役立つ、標準化された web コンテンツ管理（WCM）コンポーネントのセットです。Forms コンテナコンポーネントはコアコンポーネントです。Forms as a Cloud Service SDK のアダプティブフォームエディターでヘッドレスアダプティブフォームの JSON 構造を埋め込んでレンダリングするのに役立ちます。

### アダプティブフォーム V2 仕様

ヘッドレスアダプティブフォームの仕様では、ヘッドレスアダプティブフォームの定義に使用できるすべてのコンポーネント、制約およびメソッドに関する詳細情報が提供されます。仕様は [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 形式で入手可能です。

### HTTP API と JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) を使用すると、ヘッドレスフォームの一覧、取得、検証、送信、送信ステータスの追跡を行うことができます。[JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) は、JavaScript ベースの UI フレームワークでヘッドレスアダプティブフォームを使用するのに役立ちます。

### Visual Studio Code 拡張機能

[Visual Studio Code 拡張機能](visual-studio-code-extension-for-headless-adaptive-forms.md)は、有効な JSON 構造の作成に役立ちます。これは、JSON 構造のコンポーネントの追加、削除、名前変更などの一般的な機能に加えて、IntelliSense のサポートやフォームの JSON 構造の検証も提供します。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->