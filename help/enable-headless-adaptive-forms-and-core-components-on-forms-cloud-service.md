---
title: AEM Forms as a Cloud Service でのヘッドレスアダプティブフォームを有効にする
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: AEM Forms as a Cloud Service でヘッドレスアダプティブフォームを有効にする方法を、ステップバイステップのガイドで説明します。このチュートリアルでは、AEM Forms 環境でこの強力な機能を簡単に有効にする手順について説明します。
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
workflow-type: ht
source-wordcount: '923'
ht-degree: 100%

---

# AEM Forms as a Cloud Service でヘッドレスアダプティブフォームを有効にする {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

AEM Forms as a Cloud Service でヘッドレスアダプティブフォームを有効にすると、AEM Forms Cloud Service インスタンスを使用してヘッドレスフォームの作成、公開、複数のチャネルへの配信を開始できるようになります。ヘッドレスアダプティブフォームを使用するには、アダプティブフォームコアコンポーネントを有効にした環境が必要です。

## 検討事項

* 新しい AEM Forms as a Cloud Service プログラムを作成すると、[ヘッドレスアダプティブフォームはご利用の環境で既に有効になっています](#are-adaptive-forms-core-components-enabled-for-my-environment)。

* 古い Forms as a Cloud Service プログラム（コアコンポーネントが[有効になっていない](#enable-components)）がある場合は、[アダプティブフォームコアコンポーネントの依存関係を追加](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment)し、そのリポジトリを Cloud Service 環境にデプロイしてヘッドレスアダプティブフォームを有効にすることができます。

* 既存の Cloud Service 環境に、[コアコンポーネントベースのアダプティブフォームを作成](create-a-headless-adaptive-form.md)するオプションがある場合、ヘッドレスアダプティブフォームはご利用の環境で既に有効になっています。また、コアコンポーネントベースのアダプティブフォームを、アダプティブフォームのヘッドレス表現を必要とするチャネル（モバイル、web、ネイティブアプリ、サービスなど）に、ヘッドレスフォームとして提供できます。


>[!NOTE]
>
>
> アドビは、開発者が AEM Forms as a Cloud Service 環境でヘッドレスアダプティブフォームを有効にすることなく、ヘッドレスアダプティブフォームの開発をすぐに開始できるように、アダプティブフォーム[スターターキット（React アプリ）](create-and-publish-a-headless-form.md)を提供しています。[ヘッドレスフォームを開発するための簡単なハンズオン](create-and-publish-a-headless-form.md)の後、Forms as a Cloud Service 環境でヘッドレスアダプティブフォームを有効にすることができます。

## AEM Forms as a Cloud Service 環境でヘッドレスアダプティブフォームを有効にする

AEM Forms as a Cloud Service 環境でヘッドレスアダプティブフォームを有効にするには、以下の手順を順番どおりに実行します。


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. AEM Forms as a Cloud Service Git リポジトリを複製する {#clone-git-repository}

1. [Cloud Manager](https://my.cloudmanager.adobe.com/) にログインし、組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページから&#x200B;**パイプライン**&#x200B;カードに移動し、「**リポジトリ情報にアクセス**」ボタンをクリックして、Git リポジトリにアクセスして管理します。このページには以下の情報が含まれます。

   * Cloud Manager Git リポジトリへの URL。
   * Git リポジトリの資格情報（ユーザー名とパスワード）Git ユーザー名。

   「**パスワードを生成**」をクリックして、パスワードを表示または生成します。

1. ローカルコンピューターでターミナルまたはコマンドプロンプトを開いて、次のコマンドを実行します。

   ```Shell
   git clone [Git Repository URL]
   ```

   プロンプトが表示されたら、資格情報を入力します。リポジトリがローカルコンピューターに複製されます。


## 2. Git リポジトリにアダプティブフォームコアコンポーネントの依存関係を追加する {#add-adaptive-forms-core-components-dependencies}

1. プレーンテキストコードエディターで Git リポジトリフォルダーを開きます。例：VS Code
1. `[AEM Repository Folder]\pom.xml` ファイルを編集用に開きます。
1. `core.forms.components.version`、`core.forms.components.af.version` および `core.wcm.components.version` のコンポーネントのバージョンを、[コアコンポーネントのドキュメント](https://github.com/adobe/aem-core-forms-components)で指定されているバージョンに置き換えます。コンポーネントが存在しない場合は、これらのコンポーネントを追加します。

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![フォームのコアコンポーネントの最新バージョンについて言及](/help/assets/latest-forms-component-version.png)

1. `[AEM Repository Folder]\pom.xml` ファイルの依存関係セクションに次の依存関係を追加し、ファイルを保存します。

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

1. `[AEM Repository Folder]/all/pom.xml` ファイルを編集用として開きます。次の依存関係を `<embeddeds>` セクションに追加し、ファイルを保存します。

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
   >  `${appId}` を appId に置き換えます。
   >
   >  `${appId}` を見つけるには、`[AEM Repository Folder]/all/pom.xml` ファイル内で `-packages/application/install` を検索します。`-packages/application/install` の前のテキストが `${appId}` です。例えば、次のコードは `myheadlessform` が `${appId}` です。
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. `[AEM Repository Folder]/all/pom.xml` ファイルの `<dependencies>` セクションに、次の依存関係を追加し、ファイルを保存します。

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

1. `[AEM Repository Folder]/ui.apps/pom.xml` を開いて編集します。`af-core bundle` 依存関係を追加し、ファイルを保存します。

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

## 3. プロジェクトを更新して、最新バージョンのフォームのコアコンポーネントを含める

1. [AEM アーキタイププロジェクトフォルダー]/pom.xml を編集用に開きます。


1. ファイルを保存して閉じます。

## 4. 更新を Git リポジトリにコミットし、パイプラインを実行してリポジトリをデプロイする {#Commit-the-updates-to-your-git-repository}

1. コードを Git リポジトリにコミットするには：
   1. ターミナルまたはコマンドプロンプトを開きます。
   1. `[AEM Repository Folder]` に移動し、次のコマンドを順番に実行します。

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. ファイルが Git リポジトリにコミットされた後、[パイプラインを実行](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=ja)します。

   パイプラインが正常に実行されると、対応する環境でアダプティブフォームのコアコンポーネントが有効になります。また、アダプティブフォーム（コアコンポーネント）テンプレートと Canvas 3.0 テーマが、Forms as a Cloud Service 環境に追加され、コアコンポーネントベースのアダプティブフォームをカスタマイズして作成するオプションが提供されます。


## よくある質問 {#faq}

### コアコンポーネントとは何ですか？ {#core-components}

[コアコンポーネント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ja)は、AEM で web サイトの開発時間を短縮しメンテナンスコストを削減するための、標準化された web コンテンツ管理（WCM）コンポーネントのセットです。

### コアコンポーネントを有効にすると追加される機能は？ {#core-components-capabilities}

お使いの環境でアダプティブフォームのコアコンポーネントを有効にすると、空白のコアコンポーネントベースのアダプティブフォームテンプレートと Canvas 3.0 テーマが環境に追加されます。お使いの環境でアダプティブフォームのコアコンポーネントを有効にすると、次の操作を実行できます。

* コアコンポーネントベースのアダプティブフォームの作成。
* コアコンポーネントベースのアダプティブフォームテンプレートの作成。
* コアコンポーネントベースのアダプティブフォームテンプレート用のカスタムテーマの作成。
* コアコンポーネントベースのアダプティブフォームの JSON 表現を、フォームのヘッドレス表現を必要とするモバイル、web、ネイティブアプリ、サービスなどのチャネルに提供。

### アダプティブフォームのコアコンポーネントは、自分の環境で有効になっていますか？ {#enable-components}

お使いの環境でアダプティブフォームのコアコンポーネントが有効になっていることを確認するには、次の操作を行います。

1. [AEM Forms as a Cloud Service リポジトリを複製します](#1-clone-your-aem-forms-as-a-cloud-service-git-repository)。

1. AEM Forms Cloud Service Git リポジトリの `[AEM Repository Folder]/all/pom.xml` ファイルを開きます。

1. 次の依存関係を検索します。

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![all/pom.xml で core-forms-components-af-core アーティファクトを見つける](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   依存関係が存在する場合、お使いの環境でアダプティブフォームのコアコンポーネントが有効になります。
