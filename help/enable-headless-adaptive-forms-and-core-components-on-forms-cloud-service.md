---
title: AEM Formsas a Cloud ServiceのヘッドレスアダプティブFormsを有効にする
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: AEM Forms上のヘッドレスアダプティブフォームをas a Cloud Service的に有効にする方法については、ステップバイステップガイドを参照してください。 このチュートリアルでは、この強力な機能をAEM Forms環境で簡単に有効にできるように、プロセスについて説明します。
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7c545ca6-cb2d-4d28-b9e8-b6efe3faee00
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 7%

---

# AEM Formsas a Cloud ServiceのヘッドレスアダプティブFormsを有効にする {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

AEM Formsas a Cloud ServiceのヘッドレスアダプティブFormsを有効にすると、AEM FormsCloud Serviceインスタンスを使用して、複数のチャネルにヘッドレスFormsの作成、公開、配信を開始できます。 ヘッドレスアダプティブFormsを使用するには、アダプティブFormsコアコンポーネントが有効な環境が必要です。

## 検討事項

* 新しいAEM Formsas a Cloud Serviceプログラムを作成する場合、 [ヘッドレスアダプティブFormsは、お使いの環境で既に有効になっています](#are-adaptive-forms-core-components-enabled-for-my-environment).

* 古いFormsas a Cloud Serviceプログラム（コアコンポーネントを使用）がある場合 [無効](#enable-components)を使用する場合、 [アダプティブFormsコアコンポーネントの依存関係を追加する](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) をAEMas a Cloud Serviceリポジトリに追加し、リポジトリをCloud Service環境にデプロイして、ヘッドレスアダプティブFormsを有効にします。

* 既存のCloud Service環境で [コアコンポーネントベースのアダプティブFormsの作成](create-a-headless-adaptive-form.md)ヘッドレスアダプティブFormsは、お使いの環境で既に有効になっており、コアコンポーネントベースのアダプティブFormsを、Adaptive Formsのヘッドレス表現を必要とするモバイル、Web、ネイティブアプリ、サービスなどのチャネルにヘッドレスフォームとして提供できます。


>[!NOTE]
>
>
> AdobeがアダプティブFormsを提供 [スターターキット（React アプリ）](create-and-publish-a-headless-form.md) を使用すると、AEM Formsas a Cloud Service環境でヘッドレスアダプティブFormsを有効にすることなく、ヘッドレスアダプティブFormsの開発をすばやく開始できます。 後で、Forms as a Cloud Service環境でヘッドレスアダプティブFormsを有効にすることができます。 [ヘッドレスフォームの開発に関する簡単な実践](create-and-publish-a-headless-form.md).

## AEM Formsas a Cloud Service環境でのヘッドレスアダプティブFormsの有効化

次の手順を上の順に実行して、AEM Formsas a Cloud Service環境でヘッドレスアダプティブFormsを有効にします。


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. AEM Formsas a Cloud ServiceGit リポジトリのクローン {#clone-git-repository}

1. にログインします。 [Cloud Manager](https://my.cloudmanager.adobe.com/) 組織とプログラムを選択します。

1. 次に移動： **パイプライン** お客様の **プログラムの概要** ページで、 **リポジトリ情報にアクセス** ボタンをクリックして、Git リポジトリにアクセスして管理します。 このページには、次の情報が含まれています。

   * Cloud Manager Git リポジトリの URL。
   * Git リポジトリ（ユーザー名とパスワード）Git ユーザー名の資格情報。

   クリック **パスワードを生成** をクリックして、パスワードを表示または生成します。

1. ローカルコンピューターでターミナルまたはコマンドプロンプトを開き、次のコマンドを実行します。

   ```Shell
   git clone [Git Repository URL]
   ```

   プロンプトが表示されたら、資格情報を入力します。 リポジトリがローカルコンピューターに複製されます。


## 2. Git リポジトリにアダプティブFormsコアコンポーネントの依存関係を追加する {#add-adaptive-forms-core-components-dependencies}

1. プレーンテキストコードエディターで Git リポジトリフォルダーを開きます。 例：VS Code
1. `[AEM Repository Folder]\pom.xml` ファイルを編集用に開きます。
1. のバージョンを置き換える `core.forms.components.version`, `core.forms.components.af.version` および `core.wcm.components.version` バージョンが指定されたコンポーネント [コアコンポーネントのドキュメント](https://github.com/adobe/aem-core-forms-components). コンポーネントが存在しない場合は、これらのコンポーネントを追加します。

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![最新バージョンのForms Core Components のメンション](/help/assets/latest-forms-component-version.png)

1. の dependencies セクション `[AEM Repository Folder]\pom.xml` ファイルを作成し、次の依存関係を追加して、ファイルを保存します。

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. `[AEM Repository Folder]/all/pom.xml` ファイルを編集用として開きます。次の依存関係を `<embeddeds>` 」セクションに移動して、ファイルを保存します。

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  置換 `${appId}` を appId に置き換えます。
   >
   >  次を検索： `${appId}`、 `[AEM Repository Folder]/all/pom.xml` ファイルを検索する `-packages/application/install` 用語 次の行の前のテキスト： `-packages/application/install` 用語があなたの `${appId}`. 例えば、次のコードは `myheadlessform` 次に該当 `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Adobe Analytics の `<dependencies>` のセクション `[AEM Repository Folder]/all/pom.xml` ファイルを作成し、次の依存関係を追加して、ファイルを保存します。

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. `[AEM Repository Folder]/ui.apps/pom.xml` を開いて編集します。次を追加： `af-core bundle` 依存関係を設定し、ファイルを保存します。

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >次のアダプティブフォームのコアコンポーネントアーティファクトがプロジェクトに含まれていないことを確認します。
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > および
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. ファイルを保存して閉じます。

## 3.プロジェクトを更新して、Formsコアコンポーネントの最新バージョンを含めます。

1. を開きます。 [AEM Archetype プロジェクトフォルダー]/pom.xmlを参照してください。


1. ファイルを保存して閉じます。

## 4.更新を Git リポジトリにコミットし、パイプラインを実行してリポジトリをデプロイします {#Commit-the-updates-to-your-git-repository}

1. コードを Git リポジトリにコミットするには：
   1. ターミナルまたはコマンドプロンプトを開きます。
   1. 次の場所に移動： `[AEM Repository Folder]` をクリックし、次のコマンドをリストの順序で実行します。

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. ファイルが Git リポジトリにコミットされた後、 [パイプラインを実行](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=ja).

   パイプラインの実行が成功したら、対応する環境でアダプティブFormsコアコンポーネントが有効になります。 また、Formsas a Cloud Service環境にアダプティブForms（コアコンポーネント）テンプレートと Canvas 3.0 テーマが追加され、コアコンポーネントベースのアダプティブFormsをカスタマイズして作成するオプションが提供されます。


## よくある質問 {#faq}

### コアコンポーネントとは {#core-components}

The [コアコンポーネント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ja) は、AEMの開発時間を短縮し、Web サイトのメンテナンスコストを削減するための、標準化された Web コンテンツ管理 (WCM) コンポーネントのセットです。

### コアコンポーネントの有効化に関しては、どのような機能が追加されますか？ {#core-components-capabilities}

お使いの環境でアダプティブFormsコアコンポーネントを有効にすると、空のコアコンポーネントベースのアダプティブフォームテンプレートとキャンバス 3.0 テーマが環境に追加されます。 お使いの環境でアダプティブFormsコアコンポーネントを有効にすると、次の操作を実行できます。

* コアコンポーネントベースのアダプティブFormsを作成します。
* コアコンポーネントベースのアダプティブフォームテンプレートを作成します。
* コアコンポーネントベースのアダプティブフォームテンプレート用にカスタムテーマを作成します。
* コアコンポーネントベースのアダプティブフォームの JSON 表現を、モバイル、Web、ネイティブアプリ、フォームのヘッドレス表現を必要とするサービスなどのチャネルに提供する。

### アダプティブFormsコアコンポーネントは、自分の環境で有効になっていますか？ {#enable-components}

お使いの環境でアダプティブFormsコアコンポーネントが有効になっていることを確認するには、次の手順を実行します。

1. [AEM Forms as a Cloud Serviceリポジトリのクローン](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. を開きます。 `[AEM Repository Folder]/all/pom.xml` ファイルを作成します。AEM FormsCloud ServiceGit リポジトリの。

1. 次の依存関係を検索します。

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![all/pom.xmlで core-forms-components-af-core アーティファクトを見つけます。](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   依存関係が存在する場合、お使いの環境でアダプティブFormsコアコンポーネントが有効になります。