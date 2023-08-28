---
title: Adobe Experience Manager Adaptive Formsを使用したヘッドレスフォームの作成と発行 |ステップバイステップガイド
description: Adobe Experience Managerのアダプティブフォームを使用してヘッドレスフォームを作成して公開する方法については、この詳しい手順ガイドを参照してください。 ヘッドレスに移行してフォーム作成プロセスを効率化する利点を今すぐ確認できます。 Adobe Experience ManagerヘッドレスアダプティブFormsを使用すれば、デバイスをまたいでシームレスに動作する、動的でレスポンシブなフォームを構築できます。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 1%

---



# React アプリを使用したヘッドレスフォームの作成とプレビュー {#introduction}

スターターキットは、React アプリをすぐに使い始めるのに役立ちます。 angular、Vanilla JS、および任意の他の開発環境で、ヘッドレスアダプティブフォームを自由に開発および使用できます。

ヘッドレスアダプティブフォームを使用すると、簡単かつ迅速に作業を開始できます。 既製の React プロジェクトのクローンを作成し、依存関係をインストールして、プロジェクトを実行します。 React アプリにヘッドレスアダプティブフォームが統合され、実行されている。 サンプルの React プロジェクトを使用して、実稼働環境にデプロイする前にヘッドレスアダプティブフォームを構築し、テストすることができます。

まず始めましょう：

>[!NOTE]
>
>
> この入門ガイドでは、React アプリを使用します。 ヘッドレスアダプティブフォームを使用する場合は、任意のテクノロジーやプログラミング言語を自由に使用できます。

## 事前準備 {#pre-requisites}

React アプリを作成して実行するには、次の機能がコンピューターにインストールされている必要があります。

* をインストールします。 [Git の最新リリース](https://git-scm.com/downloads). Git を初めて使用する場合は、 [Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* インストール [Node.js 16.13.0以降](https://nodejs.org/ja/download/). Node.js を初めて使用する場合は、 [Node.js のインストール方法](https://nodejs.dev/en/learn/how-to-install-nodejs).

## はじめに

要件を満たしたら、次の手順を実行して開始します。

1. [ヘッドレスアダプティブフォームスターターキットのセットアップ](#setup)

1. [スターターキットに含まれているヘッドレスアダプティブフォームをプレビューします。](#preview)

1. [独自のヘッドレスアダプティブフォームを作成してレンダリングする](#custom)



## 1.ヘッドレスアダプティブフォームスターターキットを設定する {#install}

スターターキットは、サンプルのヘッドレスアダプティブフォームと対応するライブラリを備えた React アプリです。 このキットを使用して、ヘッドレスアダプティブフォームと対応する React コンポーネントを開発およびテストします。 ヘッドレスアダプティブフォームスターターキットを設定するには、次のコマンドを実行します。

1. コマンドプロンプトを開き、次のコマンドを実行します。

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   このコマンドは、 **react-starter-kit-aem-headless-forms** 現在の場所に Headless アダプティブフォームの React スターターアプリを複製します。 フォームのレンダリングに必要な設定と依存関係のリストに加えて、このディレクトリには次の重要なコンテンツが含まれます。

   * **サンプルフォーム**：スターターキットには、サンプルのローン申し込みフォームが含まれています。 アプリに含まれているフォーム（フォーム定義）を表示するには、 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` ファイル。
   * **React コンポーネントのサンプル**：スターターキットには、リッチテキストとスライダー用のサンプル React コンポーネントが含まれています。 このガイドでは、これらのリッチテキストコンポーネントとスライダーコンポーネントを使用して独自のカスタムコンポーネントを作成する方法について説明します。
   * **Mappings.ts**: mappings.ts ファイルは、カスタムコンポーネントをフォームフィールドにマッピングするのに役立ちます。 例えば、数値ステッパーフィールドを評価コンポーネントとマッピングします。
   * **環境設定**：環境設定を使用すると、スターターキットに含まれるフォームをレンダリングするか、AEM Forms Server からフォームを取得するかを選択できます。

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > ドキュメント内の例は VSCode に基づいています。 任意のプレーンテキストコードエディターを自由に使用できます。


1. 次に移動： **react-starter-kit-aem-headless-forms** ディレクトリに移動し、次のコマンドを実行して依存関係をインストールします。

   ```shell
   npm install
   ```

   このコマンドは、アプリの実行と構築に必要なすべてのパッケージとライブラリをダウンロードします。例えば、ヘッドレスアダプティブフォームライブラリ (@aemforms/af-react-renderer、@aemforms/af-react-components、@adobe/react-spectrum)、検証を実行し、フォームのインスタンスのデータを保持します。

   ![](/help/assets/install-react-app-starter-kit.png)


## 2.ヘッドレスアダプティブフォームのプレビュー {#preview}

スターターキットを設定した後、サンプルのヘッドレスアダプティブフォームをプレビューし、独自のカスタムフォームに置き換えることができます。 また、スターターキットを設定して、AEM Forms Server からフォームを取得することもできます。 フォームをプレビューするには

1. 名前を変更 `env_template` ～にファイルを送る `.env` ファイル。 また、USE_LOCAL_JSON オプションが true に設定されていることを確認します。

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. 次のコマンドを使用して、アプリケーションを実行します。

   ```shell
     npm start
   ```


   このコマンドは、ローカル開発サーバーを起動し、スターターアプリに含まれるサンプルのヘッドレスアダプティブフォームをデフォルトの Web ブラウザーで開きます。

   ![ヘッドレスフォームのサンプル](assets/sample-headless-adaptive-form.png)

   これです！ これで、カスタムのヘッドレスアダプティブフォームの開発を開始するための設定が整いました。

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless adaptive form on an AEM Server  -->

## 3.独自のヘッドレスアダプティブフォームを作成してレンダリングする{#custom}

ヘッドレスアダプティブフォームは、フィールドやボタンなどのフォームとそのコンポーネントを、JSON（JavaScript オブジェクト表記法）形式で表しています。 JSON 形式を使用する利点は、様々なプログラミング言語で簡単に解析および使用でき、システム間でフォームデータを交換する便利な方法になることです。 アプリに含まれているサンプルのヘッドレスアダプティブフォームを表示するには、 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` ファイル。

「名前」、「電子メール」、「連絡先番号」、「メッセージ」の 4 つのフィールドを持つ連絡先フォームを作成します。 フィールドは、JSON 内でオブジェクト（項目）として定義され、各オブジェクト（項目）には、タイプ、ラベル、名前、必須などのプロパティが含まれます。 フォームには、「送信」タイプのボタンもあります。 フォームの JSON を次に示します。


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * 「afModelDefinition」属性は、React アプリケーションに対してのみ必要で、フォーム定義の一部ではありません。
> * フォームの JSON を手作業で作成するか、 [AEMアダプティブフォームエディター（アダプティブフォームの WYSIWYG エディター）](create-a-headless-adaptive-form.md) フォーム JSON を作成して配信します。 実稼動環境では、AEM Formsを使用してフォーム JSON を後で配信します。
> * このチュートリアルでは、 https://pipedream.com/を使用してフォーム送信をテストします。 組織が承認した独自のエンドポイントまたはサードパーティのエンドポイントを使用して、ヘッドレスアダプティブフォームからデータを受け取る。


フォームをレンダリングするには、サンプルのヘッドレスアダプティブフォーム JSON を置き換えます。 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` 上記の JSON を使用して、ファイルを保存し、starter-kit がフォームをコンパイルして更新するのを待ちます。

![サンプルのヘッドレスアダプティブフォーム JSON を置き換える `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` カスタムのヘッドレスアダプティブフォーム JSON を使用する](assets/render-custom-headless-adaptive-form.png)

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

これで、ヘッドレスアダプティブフォームが正常にレンダリングされました。


## ボーナス

フォームをホストする Web ページのタイトルをに設定します。 `Contact Us | WKND Adventures and Travel`. タイトルを変更するには、 _react-starter-kit-aem-headless-forms/public/index.html_ ファイルを編集し、タイトルを設定します。

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## 次の手順

デフォルトでは、スターターキットは [Adobeスペクトル](https://spectrum.adobe.com/) フォームをレンダリングするコンポーネント。 独自のコンポーネントまたはサードパーティのコンポーネントを作成して使用できます。 例えば、Googleの素材 UI やチャクラ UI を使用します。

さあ [Google Material UI の使用](use-google-material-ui-react-components-to-render-a-headless-form.md) 「お問い合わせ」フォームをレンダリングするには、以下を実行します。




