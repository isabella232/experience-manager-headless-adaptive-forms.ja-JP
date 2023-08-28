---
title: AEM 6.5 FormsでのヘッドレスアダプティブFormsの有効化
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: 手順ガイドを使用して、AEM 6.5 Forms上でヘッドレスアダプティブフォームを有効にする方法を説明します。 このチュートリアルでは、この強力な機能を Web サイトに簡単に統合し、ユーザーエクスペリエンスを向上させるためのプロセスについて説明します。
seo-description: Learn how to enable headless adaptive forms on AEM 6.5 Forms with our step-by-step guide. Our tutorial walks you through the process, making it easy to integrate this powerful feature into your website and improve your user experience.
contentOwner: Khushwant Singh
role: Admin
exl-id: c5a7dee1-b177-4461-b9bd-af40ef59ad80
source-git-commit: f489a2ba818db44ccd92df80a177f0e9f3a1bc2c
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 5%

---

# AEM 6.5 FormsでのヘッドレスアダプティブFormsの有効化 {#enable-headless-adaptive-forms-on-aem-65-forms}

AEM 6.5 Forms環境でヘッドレスアダプティブFormsを有効にするには、AEMアーキタイプ 41 以降ベースのプロジェクトを設定し、すべてのオーサーインスタンスとパブリッシュインスタンスにデプロイします。

AEM Archetype 41 以降ベースのプロジェクトをAEM 6.5 Formsインスタンスにデプロイすると、次の操作を実行できます。 [コアコンポーネントベースのアダプティブFormsの作成](create-a-headless-adaptive-form.md). これらのフォームは JSON 形式で表され、ヘッドフルおよびヘッドレスアダプティブFormsとして使用され、モバイル、Web、ネイティブアプリなど、様々なチャネルをまたいで柔軟性とカスタマイズが可能です。

## 前提条件 {#prerequisites}

AEM 6.5 Forms環境でヘッドレスアダプティブFormsを有効にする前に、

* [AEM 6.5 Forms Service Pack 16(6.5.16.0) 以降にアップグレードします。](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html).

* 最新リリースのをインストールする [Apache Maven](https://maven.apache.org/download.cgi).

* プレーンテキストエディターをインストールします。 例： Microsoft Visual Studio Code。

## 最新のAEMアーキタイプベースのプロジェクトを作成してデプロイする

AEMアーキタイプ 41 を作成するには、以下を実行します。 [後で](https://github.com/adobe/aem-project-archetype) ベースのプロジェクトを作成し、すべてのオーサーインスタンスとパブリッシュインスタンスにデプロイします。

1. AEM 6.5 Formsインスタンスをホストし、実行しているコンピューターに、管理者としてログインします。
1. コマンドプロンプトまたはターミナルを開きます。
1. 次のコマンドを実行して、AEM Archetype 41 ベースのプロジェクトを作成します。

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.15" 
   ```

   * Linux またはApple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.15" 
   ```

   上記のコマンドを実行する際は、次の点を考慮してください。

   * appTitle、appId、groupId など、環境に固有の値を反映するようにコマンドを更新します。 また、includeFormsenrollment の値を&#39;y&#39;に設定します。 Forms Portal を使用している場合、 _includeExamples=y_ Forms Portal コアコンポーネントをプロジェクトに含めるオプション。

   * 「aemVersion」を 6.5.15.0から他のものに変更しないでください。

1. （アーキタイプバージョン 41 ベースのプロジェクトのみ）AEMアーキタイププロジェクトを作成したら、コアコンポーネントベースのアダプティブFormsのテーマを有効にします。 テーマを有効にするには：

   1. を開きます。 [AEM Archetype プロジェクトフォルダー]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html編集用：

   1. 21 行目に次のコードを追加します。

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![上記のコードを 21 行目に追加します。](/help/assets/code-to-enable-themes.png)

   1. ファイルを保存して閉じます。

1. プロジェクトを更新して、Formsコアコンポーネントの最新バージョンを含めます。

   1. を開きます。 [AEM Archetype プロジェクトフォルダー]/pom.xmlを参照してください。
   1. のバージョンを設定 `core.forms.components.version` および `core.forms.components.af.version` から [最新のFormsコアコンポーネント](https://github.com/adobe/aem-core-forms-components/tree/release/650) バージョン。

      ![最新バージョンのForms Core Components のメンション](/help/assets/latest-forms-component-version.png)

   1. ファイルを保存して閉じます。


1. AEMアーキタイププロジェクトが正常に作成されたら、環境用のデプロイメントパッケージを構築します。 パッケージをビルドするには、次の手順に従います。

   1. AEMアーキタイププロジェクトのルートディレクトリに移動します。


   1. 次のコマンドを実行して、環境用のAEM Archetype プロジェクトを構築します。

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   AEMアーキタイププロジェクトが正常に構築されたら、AEMパッケージが生成されます。 パッケージは、次の場所にあります。 [AEM Archetype プロジェクトフォルダー]\all\target\[appid].all-[version].zip

1. 以下を使用します。 [パッケージマネージャー](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=ja) をデプロイするには [AEM Archetype プロジェクトフォルダー]\all\target\[appid].all-[version]すべてのオーサーインスタンスとパブリッシュインスタンス上に.zip パッケージを作成します。

>[!NOTE]
>
>
>
>パブリッシュインスタンスのログインダイアログにアクセスして、パッケージマネージャーを通じてパッケージをインストールできない場合は、次の URL でログインしてみてください。 http://[公開サーバー URL]:[ポート]/system/console. これにより、パブリッシュインスタンスにログインでき、インストールプロセスを続行できます。


コアコンポーネントは、お使いの環境で有効になっています。 空のコアコンポーネントベースのアダプティブフォームテンプレートと Canvas 3.0 テーマが環境にデプロイされ、次の操作が可能になります。 [コアコンポーネントベースのアダプティブFormsの作成](create-a-headless-adaptive-form.md).

## よくある質問

### コアコンポーネントとは

The [コアコンポーネント](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ja) は、AEMの開発時間を短縮し、Web サイトのメンテナンスコストを削減するための、標準化された Web コンテンツ管理 (WCM) コンポーネントのセットです。

### コアコンポーネントを有効にすると、どのような機能が追加されるのですか？


お使いの環境でアダプティブFormsコアコンポーネントを有効にすると、空のコアコンポーネントベースのアダプティブフォームテンプレートとキャンバス 3.0 テーマが環境に追加されます。 お使いの環境でアダプティブFormsコアコンポーネントを有効にすると、次の操作を実行できます。

* コアコンポーネントベースのアダプティブFormsを作成します。
* コアコンポーネントベースのアダプティブフォームテンプレートを作成します。
* コアコンポーネントベースのアダプティブフォームテンプレート用にカスタムテーマを作成します。
* コアコンポーネントベースのアダプティブフォームの JSON 表現を、モバイル、Web、ネイティブアプリ、フォームのヘッドレス表現を必要とするサービスなどのチャネルに提供する。
