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
exl-id: 46df943c-0622-4b3b-a802-85c39ac6a734
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 62%

---

# コアコンポーネントとヘッドレスを使用して魅力的なフォームを構築 アダプティブForms(AEM 6.5 Forms) {#build-engaging-forms-using-core-components-and-headless}

## ラボの概要 {#lab-overview}

この実践ラボでは、次のことを学習します。

AEM Sitesと一貫性のある最新のコアコンポーネントを使用してAEM Formsを簡単にアダプティブFormsを作成する方法。アダプティブFormsをヘッドレスフォームとして Web、モバイル、チャットに提供することで、オムニチャネルのデータ取得エクスペリエンスを有効にします。 また、スタイル設定、カスタマイズ、フロントエンド開発に関するベストプラクティスについても学習します。

## 重要ポイント {#key-takeaways}

* **ビジネスの俊敏性**：ビジネスユーザーは、複数のチャネル用のフォームエクスペリエンスを簡単に作成できます。

* **フロントエンド開発者に力を与える**：フロントエンド開発者は、ヘッドレスフォームを使用してエンドユーザーエクスペリエンスを制御できます。

* **開発者の速度**：開発者は、Sites コンポーネントと Forms コンポーネントを簡単かつ一貫してカスタマイズできます。

## 事前準備 {#pre-requisites}

この手をラボで使用するには：

* をインストールします。 [Git の最新リリース](https://git-scm.com/downloads). Git を初めて使用する場合は、 [Git のインストール](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* インストール [Node.js 16.13.0以降](https://nodejs.org/ja/download/). Node.js を初めて使用する場合は、 [Node.js のインストール方法](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [ヘッドレスアダプティブFormsの有効化](enable-headless-adaptive-forms-and-core-components.md) (AEM 6.5 Forms環境で使用 )

* インストール [Microsoft Visual Studio Code](https://code.visualstudio.com/download) または任意のプレーンテキストエディター。 ドキュメントの例では、Microsoft Visual Studio Code を使用しています。

## レッスン 1 {#lesson-1}

### 目的 {#lesson-1-objectives}

AEM 6.5 Forms環境について確認します。

### レッスンのコンテキスト {#lesson-1-context}

このレッスンでは、ユーザーインターフェイスを移動してAEM 6.5 Formsに慣れています。

### 演習 {#lesson-1-excercise}

1. ブラウザーを開き、 オーサー環境の URL を入力します。例：
   [https://localhost:4502](https://localhost:4502).

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

このレッスンでは、ビジネスユーザーとして、標準化された標準コアコンポーネントを使用して Adaptive Forms Editor を使用し、Web、モバイル、チャットなど複数のチャネル用のアダプティブフォームを作成し、データを取得します。

### 演習

1. フォームの送信エンドポイントを作成します。

   1. 新しいブラウザータブで、<https://requestbin.com/> を開きます。
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. **公開 bin を作成**をクリックし、エンドポイント URL をコピーします。
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   この特定のエンドポイントは、データの送信と表示の例として機能します。 実際の実稼動環境では、独自のエンドポイントまたはデータソースを使用して、取り込んだデータを保存します。

1. アダプティブフォームの作成：

   1. レッスン 1 で使用するブラウザータブで、 AEM Forms Web インターフェイスに移動し、に移動します。 **Forms** > **Formsとドキュメント**.

   1. 「**作成**」をタップして、「アダプティブフォーム」を選択します。
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. を選択します。 **コアコンポーネントで空白** 次に示すように、テンプレートの選択画面からテンプレートを選択し、「 」をクリックします。 **次へ**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. 指定 `Contact us` として **タイトル** フォームの。 次の点を確認します。 **名前** の形式が `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. 「**作成**」をクリックします。ダイアログボックスが表示されます。

   1. ダイアログボックスで、 **編集**. アダプティブフォームエディターでフォームが開きます。 ポップアップまたはダイアログを閉じて、環境設定や情報を表示します。

   1. コンポーネントブラウザーを開き、パネルコンポーネントを画面の中央にドラッグ&amp;ドロップします。

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. コンポーネントブラウザーからコンポーネントをドラッグ&amp;ドロップして、次のようなフォームを作成します。

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. コンテンツブラウザーを開き、「Guide Container」プロパティアイコンをクリックして、 **送信** タブをクリックします。 を選択します。 **REST エンドポイントに送信** 送信アクションで、 **POST要求を有効にする** オプションを選択し、レッスン 2 で作成した REST エンドポイントを **POST要求の URL** テキストボックスをクリックし、 **完了** アイコン。

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. アダプティブフォームを発行する：

   1. AEM UI を開き、に移動します。 **Forms** > **Forms &amp; Documents**. 前の手順で作成したフォームを選択し、 **公開**.

   1. アセットを公開ダイアログで、 **公開**. 成功メッセージが表示されます。

## レッスン 3

### 目的

フロントエンド開発のベストプラクティスを使用して、スタイルを更新します。

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者が、以前に作成したアダプティブフォームのスタイル設定を簡単に更新する方法を学習します。

### 演習

テーマのローカルリポジトリを設定します。

1. 管理者権限でコマンドプロンプトまたはシェルを開きます。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用してに移動します。 `c:\git` フォルダー。

   ```Shell
   cd git
   ```

   フォルダーが存在しない場合は、 `md git` 」コマンドを使用して作成します。

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

1. 名前を変更 `env_template` ファイルを.env に変換します。  ファイル名を変更するには、**env_template** ファイルを右クリックして、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. .env ファイルの変数に次の値を設定して、ファイルを保存します。

   * **AEM_URL**：の URL を指定します。 **公開** インスタンス。 例：`https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**：フォームの名前を指定します。 例：`contact-us`

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

このレッスンでは、フロントエンド開発者として、React スペクトルデザインフレームワークを使用して、前にヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法を学びます。

### 演習

React スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用してに移動します。 `c:\git` フォルダー。

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

パブリッシュ環境でホストされるフォームをレンダリングするには：

1. env_template ファイルを.env ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」オプションを選択します。

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。

   * **AEM_URL**： パブリッシュ環境の URL を指定します。例：`https://localhost:4503/`

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。 例：`/content/forms/af/contact-us/`

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

1. ブラウザーで AEM Forms 管理インターフェイスを開きます。例： [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. を選択します。 **お問い合わせ** フォームとクリック **編集。** フォームがアダプティブFormsエディターで開きます。


1. を選択します。 **連絡先番号** フィールドに入力し、 **編集アイコン（鉛筆アイコン）** 」と入力します。 ポップアップツールバーが表示されない場合は、右上の、「**プレビュー**」ボタンの左側にある「**編集**」ボタンをクリックして、編集モードに切り替えます。

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. ラベルをに変更します。 **モバイル番号**. フォーム内の空のスペースをクリックすると、フォームに加えた変更が保存されます。

更新したフォームを公開して、変更をパブリッシュ環境に反映します。

1. 「 AEM Forms管理インターフェイス」タブで、「連絡先」フォームを選択し、 **非公開**. 「**非公開**」ボタンが表示されない場合、手順 3 に進んで変更を直接公開します。


1. 「**非公開**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ブラウザーが更新されたら、「連絡先」フォームを選択し、「 **公開**.


1. 「**公開する**」をクリックします。次のダイアログで「**閉じる**」をクリックします。

1. ヘッドレスフォームが表示された状態で、ブラウザータブを更新します。「連絡先番号」ラベルが「モバイル番号」に変更されていることに注意してください。

   ![](/help/assets/headless-adaptive-form.png)

1. **react-starter-kit-aem-headless-forms** プロジェクトの起動に使用するコマンドプロンプトウィンドウを開き、**CTRL + C** キーを押し、
「**Y**」を入力して、Enter キーを押して npm プロセスを終了します。次の一連の演習と競合しないように、npm サーバーを停止することが重要です。

1. Visual Studio Code とコマンドプロンプトウィンドウを閉じます。


## レッスン 5

### 目的

Google Material UI を使用してフォームをヘッドレスフォームとしてレンダリングする

### レッスンのコンテキスト

このレッスンでは、フロントエンド開発者がGoogle Material UI を使用して、前にヘッドレスフォームとして作成したアダプティブフォームをレンダリングする方法を学びます。

### 演習

Material UI スタータープロジェクトを使用してローカルリポジトリを設定します。

1. 管理者権限を使用してコマンドプロンプトを開きます。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. コマンドプロンプトで、次のコマンドを使用してに移動します。 `c:\git` フォルダー。

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

パブリッシュ環境でホストされるフォームをレンダリングするには：

1. **env_template** ファイルを **.env** ファイルに名前変更します。名前を変更するには、**env_template** ファイルを右クリックし、「**名前を変更**」を選択します。

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. .env ファイル内の変数に次の値を設定します。変数を更新したら、ファイルを保存します。**Ctrl + S** キーを使用してファイルを保存します。

   * **AEM_URL**： パブリッシュ環境の URL を指定します。例： [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**：前のレッスンで作成したアダプティブフォームのパスを指定します。 例： /content/forms/af/contact-us/


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

このレッスンでは、フロントエンド開発者が、ビジネスユーザーによって以前に作成されたアダプティブフォームのマテリアル UI を使用して、様々なコンポーネントの代替表現を作成する方法を学びます。

### 演習

ヘッドレスプロジェクト内のコンポーネントのバリエーションを更新します。Mterial UI のテキスト入力コンポーネントのバリアントを `OutlinedInput` に変更する手順は次のとおりです。

1. Visual Code で、`src/components/textinput/index.tsx` にある `index.tsx` ファイルを開いて、テキスト入力コンポーネントに移動します。

1. コード 104 行目の先頭に `//` を追加します。行がコメントに変換されます。

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

+++ コアコンポーネントは一般的に使用できますか？

はい、アダプティブFormsコアコンポーネントは、AEM 6.5 FormsおよびFormsでCloud Serviceとして使用できます。 アダプティブFormsコアコンポーネントを使用するには、AEM Forms 6.5 Service Pack 16 以降が必要です。

+++

+++ ヘッドレスフォームには別のライセンスが必要ですか？

いいえ、ヘッドレスフォームは同じライセンス値指標、フォーム送信数を使用します。

+++




## 次の手順

これで、アダプティブFormsを構築し、ヘッドレスフォームを使用して複数のチャネルに配信する方法を学びました。新しいスキルを活用する必要があります。 優れたデータキャプチャエクスペリエンスを作成し、大規模なエンドユーザーに提供することで、楽しみながら先に進むことができます。

## リソース

* [アダプティブフォームのコアコンポーネントの概要](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ja)

* [コアコンポーネントを使用してアダプティブフォームを作成する](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=ja)

* [コアコンポーネントベースの AF のスタイル設定を更新](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=ja)

* [ヘッドレスアダプティブフォーム](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=ja)

* [ヘッドレス React スターターキットの使用](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=ja)
