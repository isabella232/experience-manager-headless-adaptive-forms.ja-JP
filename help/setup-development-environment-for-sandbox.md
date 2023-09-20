---
title: Forms as a Cloud Service サンドボックスの開発環境のセットアップ
description: Forms as a Cloud Service サンドボックスの開発環境のセットアップ
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: ht
source-wordcount: '1248'
ht-degree: 100%

---

# Cloud Service 上にヘッドレスアダプティブフォームの開発環境をセットアップする方法

<span class="preview">これは&#x200B;**作成中**&#x200B;の記事です。</span>


Cloud Service 上でヘッドレスアダプティブフォームをビルドしテストする準備ができたら、Cloud Service プログラムのフォームを有効にし、作業を開始してください。

## 事前準備

* [Git の最新バージョン](https://git-scm.com/downloads)をローカルマシンにインストールします。Git を初めて使用する場合は、[Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) を参照してください。Git リポジトリを使用して、ローカル開発環境で開発したフォームとカスタムコードを Cloud Service 開発環境にプッシュします。

* [Node.js 16.13.0 以降](https://nodejs.org/ja/download/)をローカルマシンにインストールします。Node.js を初めて使用する場合は、[How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs) を参照してください。

* AEM as a Cloud Service プログラムの作成：[プログラムの作成](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program)記事の手順 1～7 に従って、組織に対応するプログラムを作成します。

* [Cloud Service プログラムのプレリリースチャネル](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=ja?cloud-environments)を有効にします。

## ワークフローのセットアップ

Forms as a Cloud Service サンドボックスでヘッドレスアダプティブフォームを有効にするには、AEM Cloud Service プログラムの `Forms - Digital enrolment` ソリューションを有効にし、ローカルマシン上に Archetype 37 以降をベースにしたプロジェクトを作成して、Forms as a Cloud Service 環境にプッシュします。詳しい手順は次のとおりです。

![Forms as a Cloud Service サンドボックスの開発環境をセットアップするためのワークフロー](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### 1. プログラムに対して Forms を有効にする

<table style="table-layout:auto">
<tr>
  <td>
  1. <a href="https://experience.adobe.com/" >https://experience.adobe.com/</a> にログインし、「<b>Experience Manager</b>」オプションを選択します。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.「<b>Cloud Manager</b>」オプションの「<b>起動</b>」をクリックします。組織のプログラムのリストが表示されます。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. プログラムの「...」アイコンをタップし、「<b>プログラムを編集</b>」オプションを選択します。ダイアログボックスが表示されます。 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    4. プログラムを編集ダイアログボックスで「<b>ソリューションとアドオン</b>」タブに移動し、「<b>Forms - デジタル登録</b>」オプションを選択して、「<b>更新</b>」をタップします。 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### 2. プログラムの Git リポジトリのクローンをローカルマシン上に作成する

どの AEM as a Cloud Service プログラムにも Git リポジトリがあります。Git リポジトリを使用すると、カスタムコードとアセットをローカルマシンから Cloud Service 環境にアップロードできます。セットアップ時に Git リポジトリを使用して、ヘッドレスアダプティブフォーム関連のコードやテンプレートなどの情報をローカルマシンから Cloud Service プログラムに取り込みます。カスタムコードとコンテンツをローカルマシンから Cloud Service に取り込むための最初の手順は、ローカルマシン上で Cloud Service の Git リポジトリのクローンを作成することです。

>[!INFO]
>
> Git リポジトリには常に、クローンを作成せずにコミットできます。しかし、想定外のことが起こる危険性もあります。そのため、このドキュメントではクローンを作成するアプローチを採用しています。


リポジトリのクローンを作成するには：

<table style="table-layout:fixed">
<tr>
  <td>
  1. プログラムのパイプラインボックスで、「<b>リポジトリ情報にアクセス</b>」をタップします。リポジトリ情報を含んだダイアログが表示されます 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.「<b>パスワードを生成</b>」をタップし、「<b>リポジトリ URL</b>」をコピーします。 
  </td>
  <td>
      <img alt="AEM as a Cloud Service プログラム" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    3. ローカルマシンでコマンドプロンプトを開き、フォルダーを作成して次のコマンドを実行し、要求されたリポジトリ資格情報を入力します。
 </br>
 <code> git clone [Repository URL] </code> </br></br>
 例： </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br>要求されたら、<b>リポジトリ情報</b>画面から「<b>ユーザー名</b>」と「<b>パスワード</b>」を取得します。
</td>
  <td>
     <img alt="AEM as a Cloud Service プログラム" src="assets/clone-success.png">
  </td>
</tr>
</table>


### 3. AEM アーキタイプベースのプロジェクトを作成する

アーキタイププロジェクトは、Maven ベースのテンプレートです。ヘッドレスアダプティブフォームの使用を開始するためのベストプラクティスに基づいて、最小限のプロジェクトを作成します。また、Forms as a Cloud Service のコアとなるヘッドレスアダプティブフォーム機能も含んでいます。アーキタイプ 37 以降をベースとするプロジェクトを作成しデプロイすることが必須です。
®®®
オペレーティングシステムに応じて、maven コマンドを実行して、Experience Manager Forms as a Cloud Service プロジェクトを作成します。アーキタイプバージョン 37 以降を使用します。アーキタイプの最新バージョンについては、[アーキタイプのドキュメント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ja)を参照してください。

+++ Microsoft® Windows

1. 管理者権限でコマンドプロンプトを開きます（コマンドプロンプトまたは bash シェルを管理者として実行します）。
1. 以下のコマンドを実行します。

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
     -D archetypeGroupId=com.adobe.aem ^
     -D archetypeArtifactId=aem-project-archetype ^
     -D archetypeVersion=37 ^
     -D appTitle=myheadlessform ^
     -D appId=myheadlessform ^
     -D groupId=com.myheadlessform ^
     -D includeFormsenrollment="y" ^
     -D includeFormsheadless="y" 
   ```

™™™
* `appTitle` を設定して、タイトルやコンポーネントグループを定義します。
* `appId` を設定して、Maven アーティファクト ID、コンポーネントフォルダー名、設定フォルダー名、コンテンツフォルダー名およびクライアントライブラリ名を定義します。
* `groupId` を設定して、Maven グループ ID と Java™ ソースパッケージを定義します。
* `includeFormsenrollment=y` オプションを使用して、アダプティブフォームの作成に必要なフォーム固有の設定、テーマ、テンプレート、コアコンポーネントおよび依存関係を組み込みます。
* `includeFormsheadless=y` オプションを使用して、ヘッドレスアダプティブフォーム機能の追加に必要な Forms コアコンポーネントおよび依存関係を組み込みます。このオプションを有効にすると、以下が組み込まれます。\
* [コアコンポーネント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ja)を含んだ **Blank With Core Components** テンプレート。
* フロントエンド React モジュール `ui.frontend.react.forms.af`。これは、React アプリでヘッドレスアダプティブフォームをレンダリングするのに役立ちます。

+++®®®


+++ Apple macOS または Linux®

1. ターミナルをルートユーザーとして開きます。管理者権限でコマンドを実行できるようになります。ターミナルウィンドウを開いた後に `sudo root` コマンドを使用して、管理者権限でコマンドを実行することもできます。
1. 以下のコマンドを実行します。

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
     -D archetypeGroupId=com.adobe.aem \
     -D archetypeArtifactId=aem-project-archetype \
     -D archetypeVersion=37 \
     -D appTitle=myheadlessform \
     -D appId=myheadlessform \
     -D groupId=com.myheadlessform \
     -D includeFormsenrollment="y" \
     -D includeFormsheadless="y"  
   ```

™™™
* `appTitle`を設定して、タイトルやコンポーネントグループを定義します。
* `appId` を設定して、Maven アーティファクト ID、コンポーネントフォルダー名、設定フォルダー名、コンテンツフォルダー名およびクライアントライブラリ名を定義します。
* `groupId` を設定して、Maven グループ ID と Java™ ソースパッケージを定義します。
* `includeFormsenrollment=y` オプションを使用して、アダプティブフォームの作成に必要なフォーム固有の設定、テーマ、テンプレート、コアコンポーネントおよび依存関係を組み込みます。
* `includeFormsheadless=y` オプションを使用して、ヘッドレスアダプティブフォーム機能の追加に必要な Forms コアコンポーネントおよび依存関係を組み込みます。このオプションを有効にすると、以下が組み込まれます。\
* [コアコンポーネント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ja)を含んだ **Blank With Core Components** テンプレート。
* フロントエンド React モジュール `ui.frontend.react.forms.af`。これは、React アプリでヘッドレスアダプティブフォームをレンダリングするのに役立ちます。

+++

コマンドが正常に完了すると、`appID` で指定した名前のプロジェクトフォルダーが作成されます。例えば、値 `myheadlessform` の `appID` を使用する場合は、`myheadlessform` という名前のフォルダーが作成されます。ここには、アーキタイプベースのプロジェクトが含まれます。

### 4. AEM アーキタイプベースのプロジェクトを Cloud Service 環境にプッシュする

1. Git リポジトリの内容を、アーキタイプベースのプロジェクトの内容で置き換えます。

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. コマンドプロンプトを開き、Git リポジトリフォルダーに移動し、次のコマンドをリストした順に実行して、置き換えた内容を Cloud Service 環境にアップロードします。下記のコマンドを使用する代わりに、ビジュアルエディターを使用して、内容を Cloud Service リポジトリにプッシュすることもできます。

   ```
      git add .
      git commit
      git push origin
   ```

### 5. プログラムのビルドパイプラインを実行する



<table style="table-layout:auto">
<tr>
  <td>
  1. <a href="https://experience.adobe.com/" >https://experience.adobe.com/</a> にログインし、「<b>Experience Manager</b>」オプションを選択します。
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2.「<b>Cloud Manager</b>」オプションの「<b>起動</b>」をクリックします。組織のプログラムのリストが表示されます。プログラムを開きます。 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. パイプラインの「...」アイコンをタップし、「<b>実行</b>」オプションを選択します。パイプラインを実行するように求められた場合は、「<b>実行</b>」をタップし、パイプラインの「<b>ステータス</b>」が<b>完了</b>に変わるまで待ちます。  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=ja#create-program">
      <img alt="AEM as a Cloud Service プログラム" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

これで、使用中の環境でヘッドレスアダプティブフォームを使用する準備が整いました。また、フォームの JSON 定義を Cloud Service 環境にアップロードし、それに基づいてヘッドレスアダプティブフォームを作成し、[getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm) およびその他の REST API を使用してアプリケーションやサービスでヘッドレスアダプティブフォームを使用できるようになりました。
