---
title: AEMヘッドレスアダプティブフォームの開発環境の設定
description: AEMヘッドレスアダプティブフォームの開発環境の設定
hide: true
exl-id: fd92f057-1217-42f8-a454-1bc7e3827e01
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 11%

---


# ローカル開発環境のセットアップ {#headless-adaptive-forms-setup-development-environment}

ローカルマシン上でローカル開発レスアダプティブフォームを作成し、テストするためのヘッドレス環境を設定することができます。 開発環境は、AEM SDK にインストールされたAEM SDK とAEM Forms機能アーカイブで構成されます。
<!--
 After a Headless adaptive form or related assets are ready on the local development environment, you can deploy the Headless adaptive form application to your publishing environment. -- >

You require knowledge to build application using react, Git, and Maven to use Headless adaptive forms.

<!-- 

### Download the latest version of AEM as a Cloud Service SDK or Forms feature archive (AEM Forms add-on) from Software Distribution {#software-distribution}

To download the supported version of Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on):

1. Log in to [Software Distribution](https://experience.adobe.com/#/downloads) portal with your Adobe ID.

    >[!NOTE]
    >
    > Your Adobe Organization must be provisioned for AEM as a Cloud Service to download the AEM as a Cloud Service SDK.

1. Navigate to the **[!UICONTROL AEM as a Cloud Service]** tab.
1. Sort by published date in descending order.
1. Click on the latest Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on).
1. Review and accept the EULA. Tap the **[!UICONTROL Download]** button. -->

## 必要システム構成 {#headless-adaptive-forms-system-requirements}

AEM SDK をインストールするには、ローカルマシンが次の最小要件を満たしている必要があります。

* [Java 開発キット 11](https://experience.adobe.com/#/downloads/content/software-distribution/jp/general.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&amp;1_group.propertyvalues.operation=equals&amp;1_group.propertyvalues.0_values=software-type%3Atooling&amp;fulltext=Oracle%7E+JDK%7E+11%7E&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=14)
* [Git の最新リリース](https://git-scm.com/downloads). Git を初めて使用する場合は、 [Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* [Node.js 16.13.0以降](https://nodejs.org/ja/download/). Node.js を初めて使用する場合は、 [Node.js のインストール方法](https://nodejs.dev/en/learn/how-to-install-nodejs).
* [Maven 3.6 以降](https://maven.apache.org/download.cgi). Maven を初めて使用する場合は、 [Apache Maven のインストール](https://maven.apache.org/install.html).

## 開発環境の設定 {#headless-adaptive-forms-procedure-to-setup-development-environment}

新しいローカル開発環境を設定し、それを使用してヘッドレスアダプティブフォームを開発およびテストするには、次の手順を実行します。

1. [AEMas a Cloud ServiceSDK の設定](#setup-author-instance).
1. [AEM SDK へのAEM Formsアーカイブ (AEM FormsCloud Serviceアドオン ) の追加](#add-forms-archive).

<!--

1. (Optional) [Add Forms-specific users to your local Author instance](#configure-users-and-permissions).
1. (Optional) Install [Adaptive forms builder extension for Microsoft Visual Studio Code](#microsoft-visual-studio-code-extension-for-headless-adaptive-forms). 

-->

### 1. AEMas a Cloud ServiceSDK を設定する {#setup-author-instance}

AEMas a Cloud ServiceSDK(AEM SDK) は、ヘッドレスアダプティブフォームの作成とテストを行うローカルエクスペリエンスを開発者に提供します。 AEMas a Cloud ServiceSDK を使用して、ヘッドレスアダプティブフォームの作成とプレビューの両方を行うことができ、開発に関連するほとんどの検証をローカルで実行できます。 ローカルのオーサーインスタンスを設定するには：

1. [ダウンロード](https://experience.adobe.com/#/downloads/content/software-distribution/jp/aemcloud.html) 最新 [!DNL Adobe Experience Manager] as a Cloud ServiceSDK。 「公開日」列を使用して、最新の SDK を並べ替え、簡単に見つけることができます。
.zip 形式です。 サポートされているバージョンは、aem-sdk-2022.7.8085.20220725T140323Z-220700.zip 以降です。

   ![ソフトウェア配布ポータルからAEM Cloud Service SDK をダウンロードする](assets/software-distribution.png)


1. ダウンロードした.zip ファイルをローカルマシン上のディレクトリに展開します。
1. オーサーインスタンスのインストール場所として機能するディレクトリをローカルマシン上に作成します。 例：`~/aem-sdk/author`
1. 抽出した SDK ファイルの.jar ファイルをインストール場所にコピーし、ファイルの名前をに変更します。 `aem-author-p4502.jar`. The `p4502` ファイル名の文字列は、使用するポート番号を指定します。 別のポート番号を指定することもできます。

   >[!NOTE]
   >
   > .jar ファイルをダブルクリックして開始しないでください。 その結果、 [エラー](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#troubleshooting-double-click).

1. コマンドプロンプトを開きます。
   * Windows の場合、 **管理者として実行** コマンドプロンプトを管理者モードで開くオプション
   * Linux では、必ずルートユーザーとしてターミナルウィンドウを開いてください。

1. コピーした.jar ファイルを含むインストール場所に移動し、次のコマンドを実行します。

   `java -jar aem-author-p4502.jar -r prerelease`

   ![ソフトウェア配布ポータルからAEM Cloud Service SDK をダウンロードする](assets/install-sdk.png)

   * The `-r prerelease` switch は、プレリリースおよび限定的なリリースプログラムでのみ使用可能な機能を有効にします。
   * 以下を使用できます。 `admin` 認知機能の負荷を軽減するためのローカル開発のユーザー名とパスワード。

   AEMの起動後、ログインページが Web ブラウザーで開きます。 また、アドレスでAEM SDK インスタンスのログインページを開くこともできます `http://localhost:<port>` を設定します。 例： [http://localhost:4502](http://localhost:4502).

1.  オーサーインスタンスにログインします。次をタップします。 ![ヘルプ](/help/assets/Help-icon.svg) アイコンをタップし、「Adobe Experience Managerについて」をタップし、バージョン番号にプレリリースポストフィックスが含まれていることを確認します。

   ![ のヘルプ](/help/assets/prerelease.png)

PRERELEASE ポストフィックスが表示されない場合は、サーバを停止し、 `[AEM SDK installation]/crx-quickstart folder`を開き、 AEM SDK .jar ファイルを再起動します。 `-r prerelease` スイッチ。 その他のオプションについては、 [トラブルシューティング](/help/troubleshooting.md).

### 2. AEM Formsアーカイブ (AEM FormsCloud Serviceアドオン ) をAEM SDK に追加する {#add-forms-archive}

AEM Formsas a Cloud Service機能アーカイブ (AEM FormsCloud Serviceアドオン ) は、ローカル開発環境でヘッドレスアダプティブフォームを作成するためのツールを提供します。 機能アーカイブをインストールするには：

1. 最新のをダウンロードして抽出する [!DNL AEM Forms] 機能アーカイブ (AEM Formsアドオン ) [ソフトウェア配布](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=AEM*+Forms*+add*+on*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20). 「公開日」列を使用して、最新の SDK を並べ替え、簡単に見つけることができます。 サポートされているバージョンは、aem-forms-addon-2022.07.06.02-220600以降です。

1. crx-quickstart/install ディレクトリに移動します。フォルダーが存在しない場合は作成します。
1. AEM SDK インスタンスを停止します。 AEM SDK インスタンスを実行しているコマンドプロンプトウィンドウを終了して、AEMを停止できます。
1. をコピーします。 [!DNL AEM Forms] ファイルからのアドオン機能アーカイブ `aem-forms-addon-<version>.far`手順 1 でインストールフォルダーに抽出されます。
1. 次のコマンドを使用して、AEM SDK インスタンスを再起動します。

   `java -jar aem-author-p4502.jar -r prerelease`

<!-- 

### 3. (Optional) Configure users and permissions {#configure-users-and-permissions}

Create seperate user accounts for Form Developer, Form Practitioner, and end users. These account help you test Headless adaptive forms for various types of users. To create a user account and add roles to the account:

1. Login to your AEM SDK instance.
1. Go to Tools > Security > Users and tap Create. The Create New User wizard opens.
1. In the details tab, specify an ID and Password. All other fields are optional. It is recommended to provide name and an email address.
1. In the Groups tab, search and select user-groups for a user depending on their role. The table below lists all types of users and pre-defined groups for each type of forms users based on their role:
  
    | User Type | AEM Group |
    |---|---|
    | Form developer | [!DNL forms-users] (AEM Forms Users), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], and [!DNL fdm-authors]  |
    | Customer Experience Lead or UX Designer| [!DNL forms-users], [!DNL template-authors]|
    | AEM administrator | [!DNL aem-administrators], [!DNL fd-administrators] |
    | End user| When a user must log in to view and submit an Adaptive Form, add such users to [!DNL forms-users] group. </br> When no user authentication is required to access Adaptive Forms, do not assign any group to such users.|

<!-- ### 4. (Optional) Install Visual Studio Code extension for Headless adaptive forms {#microsoft-visual-studio-code-extension-for-headless-adaptive-forms}

You can use any IDE for developing Headless adaptive forms. Adobe provides an extension for Microsoft&reg;reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms. The extension adds adaptive forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. To use the extension: 

1. Ensure [Microsoft Visual Studio Code 1.62.0 or later](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version) is installed. If you have an older version or no version installed, download the latest version from [Microsoft Website](https://code.visualstudio.com/docs/setup/setup-overview)
   >[!NOTE]
   >
   >
   > To use Visual Studio from command line on macOS, see [Launching from the command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

1. Download the [Adaptive forms builder extension](/help/assets/adaptive-form-builder-0.12.0.vsix).

1. Navigate the directory containing the *adaptive-form-builder-[version].vsix* file.

1. Run the following command or see [Install from a VSIX](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix) article for detailed instructions to install a Visual Studio Code extension from a VSIX file:

    `code -–install-extension adaptive-form-builder-[version].vsix`

    </br> Replace the [version] with actual version of the extension. For example, `code -–install-extension adaptive-form-builder-0.12.0.vsix`

    </br> 

    ![Installing extension](/help/assets/install-extension.png)

<!-- ## Create and setup a react app

Adaptive forms renderer component is a react based component. It requires a react app to run and render a Headless adaptive form. To create and setup react app:

1. Open terminal in Visual Studio code and run the following command to create a react app and installs all related dependencies:

    ```shell
    npx create-react-app [react-app-name] --scripts-version 4.0.3 --template typescript
    ```

    Where [react-app-name] represents name of the project, script version is 4.0.3, and template of type typescript. For example, the following command creates a react app named *headless-forms-demo*.

    ```shell
    npx create-react-app headless-forms-demo --scripts-version 4.0.3 --template typescript
    ```

    It may take some time to create the react app and install all the dependencies. The command creates an empty react app with latest version of react and react-dom dependencies. It does not have any artifacts related to adaptive forms renderer component.

1. Adaptive forms renderer component is based on react spectrum and requires react 16.0.0 and react-dom 16.0.0. To install react 16.0.0 and related dependencies:
    1. Open the Visual Studio code terminal Window or command prompt.
    1. Navigate to the directory of react project.  
    1. Run the following command:

        ```shell
        npm install --save react@16.0.0 react-dom@16.14.0 -force
        ```

1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/forms-super-component @aemforms/forms-react-core-components @aemforms/forms-super-component @adobe/react-spectrum @react/react-spectrum
    ```

<!-- 1. Install dependencies for adaptive forms renderer component. Packages for these dependencies are available in Adobe Artifactory. To authenticate with Adobe Artifactory and install dependencies for adaptive forms renderer component:

    1. Create environment variables ARTIFACTORY_USER and ARTIFACTORY_API_TOKEN. The ARTIFACTORY_USER stores Adobe LDAP username and ARTIFACTORY_API_TOKEN stores your [Adobe Artifactory token](https://wiki.corp.adobe.com/display/Artifactory/API+Keys)

    1. Run the following command to set NPM_TOKEN and NPM_EMAIL tokens:

        ```shell

        auth=$(curl -s -u${ARTIFACTORY_USER}:${ARTIFACTORY_API_TOKEN} https://artifactory.corp.adobe.com/artifactory/api/npm/auth)
        export NPM_TOKEN=$(echo "${auth}" | grep "_auth" | awk -F " " '{ print $3 }')
        export NPM_EMAIL=$(echo "${auth}" | grep "email" | awk -F " " '{ print $3 }')
        ```

        These tokens are required to communicated with Adobe Artifactory.

    1. Create a .npmrc file in the react project.

        ![.npmrc file](/help/assets/npmrc.png)

    1. Add the following code to the file:

        ```shell
        @aemforms:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/
        @react:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/
        @quarry:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-local/
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-loca/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/:_auth=${NPM_TOKEN}
        _auth=${NPM_TOKEN}
        email=${NPM_EMAIL}
        always-auth=true
        ```

        It defines the antifactory repositories to use for Headless adaptive forms, react, and quarry related scope.
    1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/crispr-react-bindings @aemforms/crispr-react-core-components @adobe/react-spectrum @react/react-spectrum
    ```
 
-->
ローカル環境の準備が整いました。 ヘッドレスアダプティブフォームの作成に進むことができます。
