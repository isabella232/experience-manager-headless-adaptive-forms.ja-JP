---
title: コアコンポーネントとヘッドレスを使用して魅力的なフォームを構築
seo-title: Build Engaging Forms Using Core Components and Headless
description: コアコンポーネントとヘッドレスを使用して魅力的なフォームを構築
seo-description: Build Engaging Forms Using Core Components and Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: ht
source-wordcount: '2130'
ht-degree: 100%

---

# AEM 6.5 Forms 上でコアコンポーネントとヘッドレスアダプティブフォームを使用して魅力的なフォームを作成する方法 {#build-engaging-forms-using-core-components-and-headless}

## ラボの概要 {#lab-overview}

この実践ラボでは、次のことを学習します。

AEM Forms を使用して、AEM Sites と一貫性のある最新のコアコンポーネントを使って簡単にアダプティブフォームを作成し、アダプティブフォームをヘッドレスフォームとして web、モバイル、チャットに配信することで、オムニチャネルのデータ取得エクスペリエンスを実現する方法。また、スタイル設定、カスタマイズ、フロントエンド開発に関するベストプラクティスについても学習します。

## 重要ポイント {#key-takeaways}

* **ビジネスの俊敏性**：ビジネスユーザーは、複数のチャネル用のフォームエクスペリエンスを簡単に作成できます。

* **フロントエンド開発者に力を与える**：フロントエンド開発者は、ヘッドレスフォームを使用してエンドユーザーエクスペリエンスを制御できます。

* **開発者の速度**：開発者は、Sites コンポーネントと Forms コンポーネントを簡単かつ一貫してカスタマイズできます。

## 事前準備 {#pre-requisites}

このハンズオンラボを利用するには：

* [Git の最新リリース](https://git-scm.com/downloads)をインストールします。Git を初めて使用する場合は、[Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)を参照してください。

* [Node.js 16.13.0 以降](https://nodejs.org/ja/download/)をインストールします。Node.js を初めて使用する場合は、[Node.js のインストール方法](https://nodejs.dev/en/learn/how-to-install-nodejs)を参照してください。

* AEM 6.5 Forms 環境で[ヘッドレスアダプティブフォームを有効にする](enable-headless-adaptive-forms-and-core-components.md)。

* [Microsoft Visual Studio Code](https://code.visualstudio.com/download) または任意のプレーンテキストエディターをインストールします。ドキュメントの例では、Microsoft Visual Studio Code を使用しています。

## レッスン 1 {#lesson-1}

### 目的 {#lesson-1-objectives}

AEM 6.5 Forms 環境を理解する。

### レッスンのコンテキスト {#lesson-1-context}

このレッスンでは、ユーザーインターフェイスをナビゲートして AEM 6.5 Forms を理解します。

### 演習 {#lesson-1-excercise}

1. ブラウザーを開き、オーサー環境の URL を入力します。例：
   [https://localhost:4502](https://localhost:4502)。

1. ログインした後、AEM Forms UI に移動します。**Forms** をクリックします。

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. **フォームとドキュメント**&#x200B;をクリックします。環境設定や情報に関連するポップアップを解除します。

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   使用可能なすべてのフォームが表示されます。

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## レッスン 2

### 目的

最新のコアコンポーネントを使用してアダプティブフォームを作成し、フォームを設定して送信します。

### レッスンのコンテキスト

このレッスンでは、ビジネスユーザーとして、すぐに利用可能な標準化されたコアコンポーネントを使用してデータを取得し、アダプティブフォームエディターを使用して、web、モバイル、チャットなどの複数のチャネル用のアダプティブフォームを作成します。

### 演習

1. フォームの送信エンドポイントを作成します。

   1. 新しいブラウザータブで、<https://requestbin.com/> を開きます。
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. **公開 bin を作成**をクリックし、エンドポイント URL をコピーします。
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   この特定のエンドポイントは、データを送信および表示するための例として機能します。実際の運用では、独自のエンドポイントまたはデータソースを使用して、キャプチャされたデータを保存します。

1. アダプティブフォームの作成：

   1. レッスン 1 で使用したブラウザータブで、AEM Forms web インターフェイスに移動し、**フォーム**／**フォームとドキュメント**&#x200B;に移動します。

   1. 「**作成**」をタップして、「アダプティブフォーム」を選択します。
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. 選択画面から、**コアコンポーネントを含んだ空白**&#x200B;テンプレートを選択し（下図を参照）「**次へ**」をクリックします。
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. `Contact us` を、フォームの&#x200B;**タイトル**&#x200B;として指定します。フォームの&#x200B;**名前**&#x200B;が `contact-us` であることを確認します。
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. 「**作成**」をクリックします。ダイアログボックスが表示されます。

   1. ダイアログボックスで「**編集**」をクリックします。アダプティブフォームエディターでフォームが開きます。ポップアップまたはダイアログを閉じて、環境設定や情報を表示します。

   1. コンポーネントブラウザーを開き、パネルコンポーネントを画面の中央にドラッグ＆ドロップします。

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. コンポーネントブラウザーからコンポーネントをドラッグ＆ドロップして、次のようなフォームを作成します。

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. コンテンツブラウザーを開いて、コンテナのガイドプロパティアイコンをクリックし、「**送信**」タブを開きます。「送信アクション」で「**REST エンドポイントに送信**」を選択し、「**POST リクエストを有効にする**」オプションを選択して、「**POST リクエストの URL**」テキストボックスに、レッスン 2 で作成した REST エンドポイントを指定し、「**完了**」アイコンをクリックします。

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. アダプティブフォームを公開します。

   1. AEM UI を開き、**フォーム**／**フォームとドキュメント**&#x200B;に移動します。前の手順で作成したフォームを選択し、「**公開**」をクリックします。

   1. アセットを公開ダイアログで、「**公開**」をクリックします。成功メッセージが表示されます。

## レッスン 3

### 目的

フロントエンド開発のベストプラクティスを使用して、スタイルを更新します。

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が、以前に作成したアダプティブフォームのスタイルを簡単に更新する方法を説明します。

### 演習

テーマのローカルリポジトリを設定します。

1. 管理者権限でコマンドプロンプトまたはシェルを開きます。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用して `c:\git` フォルダーに移動します。

   ```Shell
   cd git
   ```

   フォルダーが存在しない場合は、`md git` コマンドを使用してフォルダーを作成します。

1. 次のコマンドを使用して、テーマのフロントエンドコードを複製します。

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. 次のコマンドをリストに表示された順序で使用して、**aem-forms-theme-canvas** ディレクトリに移動し、Visual Studio Code を開きます。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. 「**親フォルダー内のすべてのファイルの作成者を信頼する**」を選択し、「**はい、私は作成者を信頼します**」をクリックします。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. `env_template` ファイルの名前を .env に変更します。ファイル名を変更するには、**env_template** ファイルを右クリックして、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. .env ファイルの変数に次の値を設定して、ファイルを保存します。

   * **AEM_URL**：**パブリッシュ**&#x200B;インスタンスの URL を指定します。例：`https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**：フォームの名前を指定します。例：`contact-us`

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. コマンドプロンプトウィンドウで、次のコマンドを実行します。

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * `npm notice Run npm nstall -g npm@9.6.0` コマンドを使用して npm をアップデートするように求めるメッセージが表示された場合、メッセージを無視します。
   > * ワークブックでの指示がない限り、他の npm コマンドを実行しないでください。

1. 次のコマンドを実行して、フォームをプレビューします。

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   上記のコマンドを実行したら、`webpack compiled` メッセージが表示されるまで待機します。フォームがブラウザータブに表示されます。

   >[!NOTE]
   >
   >`npm run live` コマンドを実行した後、ブラウザーで 3～4 分以上空白の画面が表示される場合は、ブラウザーの URL の `localhost` を 127.0.0.1 に変更して **Enter** キーを押します。


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. Visual Studio Code で、`PROJECT\src\site\_variables.scss` ファイルを開きます。`$error` のカラーは赤の網掛けです。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. ブラウザーでフォームを送信して、「**名前（名）**」フィールドが赤くなるのを確認します。

   ![](/help/assets/error-color-before.png)

1. **$error** の色を **#5736eb** に設定して、ファイルを保存します。

1. ブラウザーを更新し、フォームを送信します。名フィールドのエラーカラーが、それに応じて変更されました。

   ![](/help/assets/error-color-after.png)

1. コマンドプロンプトで、**Ctrl + C** キーを押して、**Y** キーを押し、**Enter** キー を押して npm プロセスを終了します。次の一連の演習と競合しないように、npm サーバーを停止することが重要です。
1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。

## レッスン 4

### 目的

フォームをヘッドレスフォームとして web／モバイルおよび他のインターフェイスにレンダリングします。

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が、React スペクトルデザインフレームワークを使用して、以前にヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法を説明します。

### 演習

React スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用して `c:\git`フォルダーに移動します。

   ```Shell
   cd git
   ```

1. 次のコマンドを使用して、アダプティブフォームの React スタータープロジェクトを複製します。

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. 次のコマンドをリストに表示された順序で使用して、**react-starter-kit-aem-headless-forms** ディレクトリに移動し、Visual Studio Code を開きます。

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Visual Studio Code ウィンドウが開きます。

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

パブリッシュ環境でホストされるフォームをレンダリングするには、次の手順に従います。

1. env_template ファイルを.env ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。

   * **AEM_URL**：パブリッシュ環境の URL を指定します。例：`https://localhost:4503/`

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。例：`/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. コマンドウィンドウを開き、**react-starter-kit-aem-headless-forms** ディレクトリにいることを確認し、次のコマンドを実行します。

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. コマンドプロンプトウィンドウで、次のコマンドを実行します。

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   上記のコマンドは、ローカル開発サーバーを起動し、AEM から取得したフォーム定義を react-spectrum フロントエンドライブラリを使ってヘッドレスでレンダリングするものです。

   >[!NOTE]
   >
   > 
   > `npm start` コマンドを実行した後、ブラウザーで 3～4 分以上空白の画面が表示される場合は、ブラウザーの URL の `localhost` を 127.0.0.1 に変更して **Enter** キーを押します。

   ![](/help/assets/headless-adaptive-form-lab.png)

サーバー上のフォームをビジネスユーザーとして変更し、ヘッドレスフォームに自動的に反映された変更を表示します。

1. ブラウザーで AEM Forms 管理インターフェイスを開きます。例：[http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments)。

1. **お問い合わせ**&#x200B;フォームを選択し、「**編集**」をクリックします。アダプティブフォームエディターでフォームが開きます。


1. 「**連絡先番号**」フィールドを選択し、ツールバーの&#x200B;**編集アイコン（鉛筆アイコン）**&#x200B;をクリックします。ポップアップツールバーが表示されない場合は、右上の、「**プレビュー**」ボタンの左側にある「**編集**」ボタンをクリックして、編集モードに切り替えます。

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. ラベルを「**携帯電話番号**」に変更しますフォーム内の空のスペースをクリックすると、フォームに加えた変更が保存されます。

更新したフォームを公開して、変更をパブリッシュ環境に反映します。

1. 「AEM Forms 管理インターフェイス」タブで、お問い合わせフォームを選択し、「**非公開**」をクリックします。「**非公開**」ボタンが表示されない場合、手順 3 に進んで変更を直接公開します。


1. 「**非公開**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ブラウザーが更新されたら、お問い合わせフォームを選択し、「**公開**」をクリックします。


1. 「**公開する**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ヘッドレスフォームが表示された状態で、ブラウザータブを更新します。「連絡先番号」のラベルが「携帯電話番号」に変更されていることに注意してください。

   ![](/help/assets/headless-adaptive-form.png)

1. **react-starter-kit-aem-headless-forms** プロジェクトの起動に使用するコマンドプロンプトウィンドウを開き、**CTRL + C** キーを押し、
「**Y**」を入力して、Enter キーを押して npm プロセスを終了します。次の一連の演習と競合しないように、npm サーバーを停止することが重要です。

1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。


## レッスン 5

### 目的

Google Material UI を使用してフォームをヘッドレスフォームとしてレンダリングする

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が Google Material UI を使用して、前の手順でヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法について説明します。

### 演習

Material UI スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用して `c:\git` フォルダーに移動します。

   ```Shell
   cd git
   ```

1. 次のコマンドをリストに表示された順序で実行して、mui という名前のフォルダーを作成し、次のコマンドを使用して mui フォルダーに移動します。

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 次のコマンドを使用して、アダプティブフォームの React スタータープロジェクトを複製します。

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. 次のコマンドをリストに表示された順序で使用して、**react-starter-kit-aem-headless-forms** フォルダーに移動し、Visual Studio Code でコードを開きます。

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

パブリッシュ環境でホストされるフォームをレンダリングするには、次の手順に従います。

1. **env_template** ファイルを **.env** ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」を選択します。

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。**Ctrl + S** キーを使用してファイルを保存します。

   * **AEM_URL**：パブリッシュ環境の URL を指定します。例：[https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。例：/content/forms/af/contact-us/


1. コマンドウィンドウを開き、**react-starter-kit-aem-headless-forms** ディレクトリにいることを確認し、次のコマンドを実行します。

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. コマンドプロンプトウィンドウで、次のコマンドを実行します。

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   このコマンドは、ローカル開発サーバーを起動し、Google Material UI フロントエンドライブラリを使用して、AEM から取得したフォーム定義をヘッドレスにレンダリングします。

   >[!NOTE]
   >
   >`npm start` コマンドを実行した後、ブラウザーで 3～4 分以上空白の画面が表示される場合は、ブラウザーの URL の `localhost` を 127.0.0.1 に変更して **Enter** キーを押します。

   ![](/help/assets/google-mui-form.png)

## レッスン 6

### 目的

Material UI コンポーネントのバリエーションを使用して、ヘッドレスフォームの代替ルックアンドフィールを作成する

### レッスンのコンテキスト

このレッスンでは、ビジネスユーザーが以前に作成したアダプティブフォームに対して、フロントエンド開発者が Material UI を使用して、様々なコンポーネントの代替表現を作成する方法について説明します。

### 演習

ヘッドレスプロジェクト内のコンポーネントのバリエーションを更新します。Mterial UI のテキスト入力コンポーネントのバリアントを `OutlinedInput` に変更する手順は次のとおりです。

1. Visual Code で、`src/components/textinput/index.tsx` にある `index.tsx` ファイルを開いて、テキスト入力コンポーネントに移動します。

1. コード 104 行目の先頭に `//` を追加します。その行がコメントに変換されます。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 別のバリアントのコンポーネントを使用するために、105 行目に次のコードを追加して、ファイルを保存します。**Ctrl + S** キーを使用してファイルを保存します。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   「OutlinedInput」バリアントは正しく大文字と小文字を使用する必要があります。さもないと、コンパイルが失敗します。ローカル開発環境のコンパイルは、コマンドプロンプトで自動的に開始されます。次のメッセージが表示されるまで待ちます

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 自動的に更新されない場合は、ブラウザーを更新し、テキスト入力コンポーネントが別のバリアントを使用していることを確認します。

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   この変更は、エンドユーザーに対して AEM Forms Server のフォーム定義に変更を加えずに行われ、検討中のヘッドレスチャネルに固有のものです。
例えば、このラボの web チャネルです。

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。

## よくある質問（FAQ）

+++ コアコンポーネントは一般公開されていますか？

はい、アダプティブフォームのコアコンポーネントは、AEM 6.5 Forms および AEM Forms as a Cloud Service で使用できます。アダプティブフォームのコアコンポーネントを使用するには、AEM Forms 6.5 サービスパック 16 以降が必要です。

+++

+++ ヘッドレスフォームには別のライセンスが必要ですか？

いいえ、ヘッドレスフォームは同じライセンス値指標、フォーム送信数を使用します。

+++




## 次の手順

アダプティブフォームの構築方法と、ヘッドレスフォームを使用して複数のチャネルにアダプティブフォームを配信する方法の説明は以上です。新しいスキルを活用してみましょう。優れたデータキャプチャエクスペリエンスを作成し、大規模なエンドユーザーに提供することで、楽しみながら先に進むことができます。

## リソース

* [アダプティブフォームのコアコンポーネントの概要](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ja)

* [コアコンポーネントを使用してアダプティブフォームを作成](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=ja)

* [コアコンポーネントベースの AF のスタイル設定を更新](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=ja)

* [ヘッドレスアダプティブフォーム](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=ja)

* [ヘッドレス React スターターキットの使用](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=ja)
