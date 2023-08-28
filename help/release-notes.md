---
title: AEMヘッドレスアダプティブフォームの概要
description: AEMヘッドレスアダプティブフォームの概要です。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 3%

---


# リリースノート

このたびは、Experience Managerヘッドレスアダプティブフォームのアーリーアダプターリリースをご利用いただき、誠にありがとうございます。 このリリースを最大限に活用するためのリソースと手順については、以降の説明を参照してください。

Adobe Experience Managerヘッドレスアダプティブフォームを使用すると、React、Angularなどのフロントエンド UI フレームワークを使用してフォームアプリケーションを作成し、Adaptive Forms Web SDK を使用して、状態管理、検証、他の様々なタッチポイントとの統合などの機能を実行できます。

アーリーアダプターリリースでは、 [ローカル開発環境](setup-development-environment.md). ローカル開発環境を使用して、ヘッドレスアダプティブフォームを作成し、テストすることができます。

ヘッドレスアダプティブフォームは継続的に改善を受けます。 最新の開発状況を確認するには、このページに定期的にアクセスしてください。このページでは、早期アクセス、最新リリース、新機能、改善点、バグ修正、非推奨（廃止予定）の機能、特別な手順、今後の変更計画に関する情報を提供します。

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

## アーリーアダプターリリースで利用可能なアーティファクト

Adobe Experience Managerヘッドレスアダプティブフォームを初めてご利用いただく際には、次のアーティファクトがアーリーアダプターリリースで利用可能になります。

### AEM Formsas a Cloud ServiceSDK

ヘッドレスアダプティブフォームの作成、保存、取得に役立つAEM Formsas a Cloud ServiceSDK。 また、事前入力、サーバー側のルール検証、ヘッドレスアダプティブフォームの送信サービスを提供するのにも役立ちます。

### Forms Web SDK

Forms Web SDK は、フォームの様々なフィールドに適用された制約を検証する API を提供し、フォームの JSON 構造を UI フレームワークに接続するフックを提供します。 また、ヘッドレスアダプティブフォームをアプリケーションに統合する際に役立つヘッドレスアダプティブフォーム用の React レンダラも提供されま&#x200B;す。 Web SDK の次のコンポーネントを使用できます。

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) では、ヘッドレスアダプティブフォームの様々なコンポーネントの概要を説明しています。 また、サポートされるすべてのコンポーネント、対応するプロパティ、制約のリストも表示されます。

### Forms Core Component

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

コアコンポーネントは、開発時間の短縮とフォームのメンテナンスコストの削減に役立つ、標準化された Web コンテンツ管理 (WCM) コンポーネントのセットです。 Formsコンテナコンポーネントは、コアコンポーネントです。 これにより、Formsas a Cloud ServiceSDK のアダプティブFormsエディターにヘッドレスアダプティブフォームの JSON 構造を埋め込み、レンダリングすることができます。

### アダプティブForms V2 仕様

ヘッドレスアダプティブフォームの仕様では、ヘッドレスアダプティブフォームの定義に使用できるすべてのコンポーネント、制約、メソッドに関する詳細情報が提供されます。 仕様は、 [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 形式を使用します。

### HTTP および JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) ヘッドレスフォームの送信ステータスのリスト、取得、検証、送信、追跡を行うことができます。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) は、ヘッドレスアダプティブフォームを JavaScript ベースの UI フレームワークと共に使用する際に役立ちます。

### Visual Studio Code 拡張機能

[Visual Studio Code 拡張機能](visual-studio-code-extension-for-headless-adaptive-forms.md) 有効な JSON 構造を作成するのに役立ちます。 フォームの JSON 構造に対する IntelliSense のサポートと検証を提供し、JSON 構造のコンポーネントの追加、削除、名前変更などの一般的な関数を提供します。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->