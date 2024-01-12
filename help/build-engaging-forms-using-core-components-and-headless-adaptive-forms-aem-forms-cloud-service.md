---
title: コアコンポーネントとヘッドレスを使用して魅力的なフォームを構築
seo-title: Build Engaging Forms Using Core Components and Headless
description: コアコンポーネントとヘッドレスを使用して魅力的なフォームを構築
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: 2332af82ea221086c3b014989651e34726040ba2
workflow-type: ht
source-wordcount: '2398'
ht-degree: 100%

---

# AEM Forms as a Cloud Service 上でコアコンポーネントとヘッドレスアダプティブフォームを使用して魅力的なフォームを作成する方法 {#build-engaging-forms-using-core-components-and-headless}

## ラボの概要 {#lab-overview}

この実践ラボでは、次のことを学習します。

AEM Forms を使用して、AEM Sites と一貫性のある最新のコアコンポーネントを使って簡単にアダプティブフォームを作成し、アダプティブフォームをヘッドレスフォームとして web、モバイル、チャットに配信することで、オムニチャネルのデータ取得機能を有効にする方法。また、スタイル設定、カスタマイズ、フロントエンド開発に関するベストプラクティスについても学習します。

## 重要ポイント {#key-takeaways}

* **ビジネスの俊敏性**：ビジネスユーザーは、複数のチャネル用のフォームエクスペリエンスを簡単に作成できます。

* **フロントエンド開発者に力を与える**：フロントエンド開発者は、ヘッドレスフォームを使用してエンドユーザーエクスペリエンスを制御できます。

* **開発者の速度**：開発者は、Sites コンポーネントと Forms コンポーネントを簡単かつ一貫してカスタマイズできます。

## 前提条件 {#prerequisites}

このハンズオンラボを利用するには：

* [Git の最新リリース](https://git-scm.com/downloads)をインストールします。Git を初めて使用する場合は、[Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)を参照してください。

* [Node.js 16.13.0 以降](https://nodejs.org/ja/download/)をインストールします。Node.js を初めて使用する場合は、[Node.js のインストール方法](https://nodejs.dev/en/learn/how-to-install-nodejs)を参照してください。

* AEM Forms as a Cloud Service 環境での[アダプティブフォームコアコンポーネントの有効化。](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md)

* [Microsoft Visual Studio Code](https://code.visualstudio.com/download) または任意のプレーンテキストエディターをインストールします。ドキュメントの例では、Microsoft Visual Studio Code を使用しています。



## レッスン 1 {#lesson-1}

### 目的 {#lesson-1-objectives}

AEM Forms as a Cloud Service 環境に慣れる。

### レッスンのコンテキスト {#lesson-1-context}

このレッスンでは、ユーザーインターフェイスをナビゲートして、AEM Forms as a Cloud Service の環境に慣れ親しみます。

### 演習 {#lesson-1-excercise}

1. ブラウザーを開き、Cloud Service オーサー環境の URL を入力します。次に例を示します。
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Cloud Service オーサー環境にログインします。

1. AEM Forms UI に移動するには、**Forms／フォームとドキュメント**&#x200B;をクリックします。

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   環境設定や情報に関連するポップアップを解除します。使用可能なすべてのフォームが表示されます。


## レッスン 2

### 目的

最新のコアコンポーネントを使用してアダプティブフォームを作成し、フォームを設定して送信します。

### レッスンのコンテキスト

このレッスンでは、ビジネスユーザーとして、データ取得用の標準化された OOTB コアコンポーネントを使用して作成されたアダプティブフォームを使用して、web、モバイル、チャットなど複数のチャネル用のアダプティブフォームを作成します。

### 演習

1. フォームの送信エンドポイントを作成します。

   1. 新しいブラウザータブで、<https://requestbin.com/> を開きます。
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. **公開 bin を作成**をクリックし、エンドポイント URL をコピーします。
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. ウィザードインターフェイスを使用してアダプティブフォームを作成します。

   1. レッスン 1 で使用したブラウザータブで、AEM Forms as a Cloud Service web インターフェイスに移動し、フォーム＆ドキュメントに移動します。
      ![](/help/assets/screenshot2028114029.png)

   1. 「**作成**」をタップして、「アダプティブフォーム」を選択します。
      ![](/help/assets/screenshot2028114629.png)

   1. 選択画面から、**コアコンポーネントを使用した空白**テンプレートを選択します（下図を参照）。
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. 「**スタイル**」タブをクリックし、「**wknd-theme**」テーマを選択します（下図を参照）。
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 「**送信**」タブをクリックし、「**REST エンドポイントに送信**」カードを選択し、
      「**POST リクエストの URL**」フィールドで公開 bin を指定します（下図を参照）。
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. 「**作成**」をクリックします。フォームの名前とタイトルを指定します。例えば、**登録**&#x200B;などです。「**作成**」をクリックします。

   1. アダプティブフォームエディターが開きます。ポップアップまたはダイアログを閉じて、環境設定や情報を表示します。左側のレールにあるコンポーネントブラウザーをクリックし、**ヘッダー**&#x200B;コンポーネントと&#x200B;**フッター**コンポーネントをそれぞれ空白のフォームの上部と下部に追加します。
      ![](/help/assets/screenshot2028121929.png)

   1. コンポーネントブラウザーからコンポーネントをドラッグ＆ドロップして、次のようなフォームを作成します。

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}





1. フォームに検証機能を追加します。

   1. **電話番号**&#x200B;コンポーネントをクリックして、ポップアップメニューを表示します。**レンチアイコン**&#x200B;をクリックして、フィールドを設定します。

   1. **「検証」タブ**&#x200B;を開き、フィールドに&#x200B;**必須**&#x200B;とマークを付け、「**完了**」をクリックします。成功メッセージが表示されます。
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. フォームをプレビューして送信します.

   1. 「**プレビュー**」をクリックして、エンドユーザーの観点からフォームをプレビューします。

   1. ダミーデータでフォームに入力します。

   1. フォームを送信します。
      ![](/help/assets/screenshot2028125729.png)

   1. 「リクエスト bin」タブで、送信されたデータを確認します。
      ![](/help/assets/screenshot2028125829.png)

1. ルールを使用してフォームにインタラクティビティを追加します。

   1. 「**チェックボックスをオンにして 5％オフを受け取る**」コンポーネントをクリックします。オプションツールバーで、ルールアイコンをクリックします。「ルールエディター」オプションが開きます。

   1. ルールを作成します。「**チェックボックスをオンにして 5％オフを受け取ります**」オプションが選択されている場合、クレジットカードを適用するオプションは無効になります。

1. フォームを公開します。

   1. AEM Forms 管理インターフェイス（例：`https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`）を開き、フォームを選択します。

   1. 「**公開する**」をクリックします。

      ![](/help/assets/screenshot2028115629.png)

      成功メッセージが表示されます。

      ![](/help/assets/screenshot2028115729.png)

      フォームの公開 URL は、次のようになります。`https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`

   1. 公開されたフォームを表示するには、上記の URL のプログラム ID（pXXXXXX）と環境 ID（eXXXXXX）を、お使いの環境の ID に置き換えます。


## レッスン 3

### 目的

フロントエンド開発のベストプラクティスを使用して、スタイルを更新します。

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が、以前に作成したアダプティブフォームのスタイル設定を簡単に更新する方法を学習します。

### 演習

テーマのローカルリポジトリを設定します。

1. 管理者権限でコマンドプロンプトまたはシェルを開きます。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用して **c:\git** フォルダーに移動します。

   ```Shell
   cd c:\git
   ```

1. 次のコマンドを使用して、テーマのフロントエンドコードを複製します。

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 次のコマンドをリストに表示された順序で使用して、**aem-forms-theme-canvas** ディレクトリに移動し、Visual Studio Code を開きます。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. 「**親フォルダー内のすべてのファイルの作成者を信頼する**」を選択し、「**はい、私は作成者を信頼します**」をクリックします。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. クラウドサービスのパブリッシュ環境でホストされているフォームをレンダリングするには、`env_template` ファイルの名前を変更します。ファイル名を変更するには、**env_template** ファイルを右クリックして、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. .env ファイルの変数に次の値を設定して、ファイルを保存します。

   * **AEM_URL**：クラウドサービスのパブリッシュ環境を指定します。例：`https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**：フォームのパスを指定します。例えば、フォームのパスが `/content/forms/af/registration` の場合、この変数の値は `registration` になります。

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}


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


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. Visual Studio Code で、`PROJECT\src\site\_variables.scss` ファイルを開きます。`$error` のカラーは赤の網掛けです。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. ブラウザーでフォームを送信して、「**名前（名）**」フィールドが赤くなるのを確認します。

   ![](/help/assets/screenshot2028120829.png)

1. **$error** の色を **#5736eb** に設定して、ファイルを保存します。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. ブラウザーを更新し、フォームを送信します。名フィールドのエラーカラーが、それに応じて変更されました。

   ![](/help/assets/screenshot2028121129.png)

1. コマンドプロンプトで、**Ctrl + C** キーを押して、**Y** キーを押し、**Enter** キー を押して npm プロセスを終了します。次の一連の演習と競合しないように、npm サーバーを停止することが重要です。
1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。

## レッスン 4

### 目的

フォームをヘッドレスフォームとして web／モバイルおよび他のインターフェイスにレンダリングします。

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者として、React スペクトルデザインフレームワークを使用して、前にヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法を学びます。

### 演習

React スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用して **c:\git** フォルダーに移動します。

   ```Shell
   cd c:\git
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

クラウドサービスのパブリッシュ環境でホストされるフォームをレンダリングするには、次の手順に従います。

1. env_template ファイルを.env ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。

   * **AEM_URL**：クラウドサービスパブリッシュ環境の URL を指定します。例：`https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。例：`/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. コマンドウィンドウを開き、react-starter-kit-aem-headless-forms ディレクトリにいることを確認し、次のコマンドを実行します。

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. コマンドプロンプトウィンドウで、次のコマンドを実行します。

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   上記のコマンドは、ローカル開発サーバーを起動し、AEM から取得したフォーム定義を react-spectrum フロントエンドライブラリを使ってヘッドレスでレンダリングするものです。

   >[!NOTE]
   >
   > 
   > `npm start` コマンドを実行した後、ブラウザーで 3～4 分以上空白の画面が表示される場合は、ブラウザーの URL の `localhost` を 127.0.0.1 に変更して **Enter** キーを押します。

   ![](/help/assets/screenshot2028118229.png)

このヘッドレスフォームのルールの実行を確認しましょう。

1. 「**チェックボックスをオンにして 5％オフを受け取る**」オプションを選択します。クレジットカードを適用する後続のオプションは無効になります。

   ![](/help/assets/screenshot2028126229.png)

1. 「**チェックボックスをオンにして 5％オフを受け取る**」のチェックを解除して、クレジットカードオプションを有効にします。

   ![](/help/assets/screenshot2028126329.png)

サーバー上のフォームをビジネスユーザーとして変更し、ヘッドレスフォームに自動的に反映された変更を表示します。

1. ブラウザーで AEM Forms 管理インターフェイスを開きます。例：[https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments)

1. **お問い合わせ**&#x200B;フォームを選択し、「**編集**」をクリックします。アダプティブフォームエディターでフォームが開きます。


1. 「**電話番号**」フィールドを選択し、ツールバーの&#x200B;**編集アイコン（鉛筆アイコン）**&#x200B;をクリックします。ポップアップツールバーが表示されない場合は、右上の、「**プレビュー**」ボタンの左側にある「**編集**」ボタンをクリックして、編集モードに切り替えます。

   ![](/help/assets/screenshot2028119629.png)

1. ラベルを「携帯電話番号」に変更します。フォーム内の空のスペースをクリックすると、フォームに加えた変更が保存されます。

   ![](/help/assets/screenshot2028119729.png)

更新したフォームを公開して、変更をパブリッシュ環境に反映します。

1. 「AEM Forms 管理インターフェイス」タブで、登録フォームを選択し、「**非公開**」をクリックします。「**非公開**」ボタンが表示されない場合、手順 3 に進んで変更を直接公開します。

1. 「**非公開**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ブラウザーが更新されたら、登録フォームを選択し、「**公開**」をクリックします。

1. 「**公開する**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ヘッドレスフォームが表示された状態で、ブラウザータブを更新します。「電話番号」のラベルが「携帯電話番号」に変更されていることに注意してください。

   ![](/help/assets/screenshot2028120529.png)

1. **react-starter-kit-aem-headless-forms** プロジェクトの起動に使用するコマンドプロンプトウィンドウを開き、**CTRL + C** キーを押し、
「**Y**」を入力して、Enter キーを押して npm プロセスを終了します。次の一連の演習と競合しないように、npm サーバーを停止することが重要です。

1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。


## レッスン 5

### 目的

Google Material UI を使用してフォームをヘッドレスフォームとしてレンダリングする

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が Google Material UI を使用して、前の手順でヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法を学びます。

### 演習

Material UI スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. コマンドプロンプトで、次のコマンドを使用して **c:\git** フォルダーに移動します。

   ```Shell
   cd c:\git
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

クラウドサービスのパブリッシュ環境でホストされるフォームをレンダリングするには、次の手順に従います。

1. **env_template** ファイルを **.env** ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」を選択します。

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。**Ctrl + S** キーを使用してファイルを保存します。

   * **AEM_URL**：クラウドサービスパブリッシュ環境の URL を指定します。例：[https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。例：/content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. コマンドウィンドウを開き、**react-starter-kit-aem-headless-forms** ディレクトリにいることを確認し、次のコマンドを実行します。

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. コマンドプロンプトウィンドウで、次のコマンドを実行します。

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   このコマンドは、ローカル開発サーバーを起動し、Google Material UI フロントエンドライブラリを使用して、AEM から取得したフォーム定義をヘッドレスにレンダリングします。


   >[!NOTE]
   >
   >`npm start` コマンドを実行した後、ブラウザーで 3～4 分以上空白の画面が表示される場合は、ブラウザーの URL の `localhost` を 127.0.0.1 に変更して **Enter** キーを押します。

   ![](/help/assets/screenshot2028127229.png)

1. このフォームレンディションで同じビジネスロジックの実行を評価するには：

   「**チェックボックスをオンにして 5%オフを受け取る**」を選択します。後続のオプション「**We.Finance のコーポレートクレジットカードフォームを申し込みますか？**」が無効になります。

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## レッスン 6

### 目的

Material UI コンポーネントのバリエーションを使用して、ヘッドレスフォームの代替ルックアンドフィールを作成する

### レッスンのコンテキスト

このレッスンでは、ビジネスユーザーが以前に作成したアダプティブフォームに対して、フロントエンド開発者が Material UI を使用して、様々なコンポーネントの代替表現を作成する方法を学びます。

### 演習

ヘッドレスプロジェクト内のコンポーネントのバリエーションを更新します。Mterial UI のテキスト入力コンポーネントのバリアントを `OutlinedInput` に変更する手順は次のとおりです。

1. Visual Code で、`src/components/textinput/index.tsx` にある `index.tsx` ファイルを開いて、テキスト入力コンポーネントに移動します。

1. コード 103 行目の先頭に `//` を追加します。行がコメントに変換されます。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 別のバリアントのコンポーネントを使用するために、104 行目に次のコードを追加して、ファイルを保存します。**Ctrl + S** キーを使用してファイルを保存します。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   「OutlinedInput」バリアントは正しく大文字と小文字を使用する必要があります。さもないと、コンパイルが失敗します。ローカル開発環境のコンパイルは、コマンドプロンプトで自動的に開始されます。次のメッセージが表示されるまで待ちます

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 自動的に更新されない場合は、ブラウザーを更新し、テキスト入力コンポーネントが別のバリアントを使用していることを確認します。

   ![](/help/assets/screenshot2028127729.png)


   この変更は、エンドユーザーに対して AEM Forms Server のフォーム定義に変更を加えずに行われ、検討中のヘッドレスチャネルに固有のものです。
例えば、このラボの web チャネルです。

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。

## よくある質問（FAQ）

+++ アダプティブフォームウィザードは一般に使用できますか？

はい、AEM Forms as a Cloud Service で使用できます。

+++


+++ コアコンポーネントは一般公開されていますか？

はい、アダプティブフォームのコアコンポーネントは、AEM Forms as a Cloud Service で使用できます。

+++

+++ ヘッドレスフォームは公開されていますか？

はい、ヘッドレスフォームは、AEM Forms as a Cloud Service で使用できます。

+++

+++ ヘッドレスフォームには別のライセンスが必要ですか？

いいえ、ヘッドレスフォームは同じライセンス値指標、フォーム送信数を使用します。

+++

+++ コアコンポーネントとヘッドレスフォームは AEM 6.5 Forms で利用できますか？

はい。アダプティブフォームのコアコンポーネントとヘッドレスフォームは、AEM Forms 6.5 サービスパック 16 以降で使用できます。

+++


## 次の手順

アダプティブフォームの構築方法と、ヘッドレスフォームを使用して複数のチャネルにアダプティブフォームを配信する方法の説明は以上です。新しいスキルを活用してみましょう。優れたデータキャプチャエクスペリエンスを作成し、大規模なエンドユーザーに提供することで、楽しみながら先に進むことができます。

## リソース

* [アダプティブフォームのコアコンポーネントの概要](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ja)

* [コアコンポーネントを使用してアダプティブフォームを作成](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=ja)

* [コアコンポーネントベースの AF のスタイル設定を更新](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=ja)

* [ヘッドレスアダプティブフォーム](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=ja)

* [ヘッドレス React スターターキットの使用](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=ja)
