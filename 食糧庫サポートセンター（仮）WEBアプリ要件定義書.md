## 食糧サポートセンター（仮称）WEBアプリ

# 要件定義書

（日付）　版

# 目次

[システム化の目的と範囲	3](#システム化の目的と範囲)

[目的	3](#目的)

[業務要件（一覧）	4](#業務要件（一覧）)

[業務要件（フロー図）	5](#業務要件（フロー図）)

[機能要件（一覧）	6](#機能要件（一覧）)

[補足	7](#補足)

[非機能要件	8](#非機能要件)

[非機能要件：可用性	9](#非機能要件：可用性)

[非機能要件：性能	9](#非機能要件：性能)

[非機能要件：セキュリティ	9](#非機能要件：セキュリティ)

[非機能要件：移行性	9](#非機能要件：移行性)

[非機能要件：プロジェクト上の留意事項	10](#非機能要件：プロジェクト上の留意事項)

[プロジェクトスケジュール	12](#プロジェクトスケジュール)

[プロジェクト体制	12](#プロジェクト体制)

[メモ書き	13](#メモ書き)

# システム化の目的と範囲 {#システム化の目的と範囲}

## 目的 {#目的}

### 自炊を行う人を対象に、冷蔵および常温保管の食材管理を効率化し、以下の課題を解決するためのWEBアプリケーションを開発します。

#### 必須の課題解決:

1. **食材ロス削減**：食材の消費期限や在庫を管理し、無駄な廃棄を減らします。  
2. **家計管理の効率化**：食費を記録・可視化し、月ごとの支出や予算を簡単に把握できます。  
3. **時間の節約**：食材や消費期限の管理を効率的に行い、買い物や献立の計画を簡便にします。

   #### 追加要素（発展的な課題解決）

1. **リマインダー機能**：食材の消費期限に合わせてリマインダーを通知。  
2. **在庫の数量管理**：食材の在庫数を管理し、補充が必要なタイミングを知らせます。  
3. **買い物リストの自動生成**：過去の購入履歴に基づいて自動的に買い物リストを作成します。

### 発展的な展望

本アプリは、食材管理を通じた廃棄ロス削減や効率化を目指します。将来的には、クロスプラットフォーム対応やオフライン機能を追加することで、より多くのユーザーに対応できるようにします。

### 学習目的の技術選定

ポートフォリオとしての開発であり、無料または低コストのツール・フレームワークを使用します。将来的な拡張性や保守性を意識して設計します。

# 

# 業務要件（一覧） {#業務要件（一覧）}

| 管理番号 | 業務 | 説明 | 実施者 | システム化対策 |
| :---: | :---: | ----- | :---: | :---: |
| BR-1 | 消費期限管理 | 食材の消費期限や賞味期限を管理し、期限切れ防止を目的とする。 | User | 〇 |
| BR-2 | 食費管理 | 月間の食費を記録・可視化し、予算内での食費コントロールを支援する。 | User | 〇 |
| BR-3 | 食材補充支援 | 過去の購入履歴を基にリストを作成し、買い忘れを防止する。 | User | 〇 |
| BR-４ | 通知設定 | 通知タイミングや内容をユーザーがカスタマイズできるようにする。 | User | 〇 |
| BR-5 | データ保存・管理 | 登録したデータを保存し、編集・削除できるようにする。Undo機能も追加。 | User | 〇 |

# 

# 業務要件（フロー図） {#業務要件（フロー図）}

### 本アプリは以下の業務を実現するものとする

### ![][image1]

# 

# 機能要件（一覧） {#機能要件（一覧）}

| 管理番号 | 機能 | 説明 | 分岐 | 対応業務要件 | 備考 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| FR-1 | 消費期限通知 | 消費期限や賞味期限が近づくと通知を送信する。[^1] | 通知方法（LINE/App） | BR-1 | LINE Notify利用予定 |
| FR-2 | 食費記録機能 | 食品・食事の支出を手動入力し、グラフや一覧形式で可視化する。 | 月別、カテゴリー別 | BR-2 |  |
| FR-3 | 補充リスト作成 | 過去の購入履歴を基に買い忘れ防止用リストを作成する。 | アイテムの選択方式 | BR-3 |  |
| FR-4 | データ管理 | 食材情報の登録、編集、削除ができる機能。 | 処理の種類（CRUD） | BR-5 |  |
| FR-5 | 通知設定機能 | 通知のタイミングや内容をカスタマイズする設定画面を提供する。 | タイミング（1日前等） | BR-4 |  |

# 補足 {#補足}

### 対象ユーザー

* 新社会人や一人暮らしの自炊をしている人。

### 利用環境

* Reactを用いたクロスプラットフォーム対応（Webアプリ中心）。

### データベース

* H2を採用し、シンプルでコストを抑えたデータ管理を実現。

# 

# 非機能要件 {#非機能要件}

| 非機能要件 | 管理番号 | 個別定義対象 | 内容 |
| :---: | :---: | :---: | ----- |
| 可用性 | NR-１ | 〇 | アプリは常にアクセス可能で、通知機能が指定された時間に確実に動作することを保証。 |
| 性能 | NR-2 | 〇 | 食材の登録、編集、削除、通知処理などの操作が即時に反映され、スムーズな操作感を提供。 |
| セキュリティ | NR-3 | ー | **LINE Notify連携**:  トークンの不正利用を防ぐため、暗号化技術を使用し、安全性を確保。SSL/TLSでデータ保護。 **データ保護**:  食材情報や食費データは暗号化して保存。 |
| 移行性 | NR-4 | ー | クロスプラットフォーム対応を前提に、スマートフォン向けアプリに移行しやすい設計を採用（React Native）。 |
| プロジェクト上の留意事項 | NR-5 | 〇 | ポートフォリオ用のプロジェクトであるため、無料または低コストのクラウドサービス・技術を採用。 |

# 非機能要件：可用性 {#非機能要件：可用性}

### 　高可用性

* ローカルデータ保存機能を持つため、オフライン時にはデータの閲覧が可能で、オンライン復帰後に自動でデータが同期される機能を実装する。

### 　通知機能

* LINE通知でユーザーに確実に情報を届ける。

# 非機能要件：性能 {#非機能要件：性能}

### レスポンス時間

* 登録、編集、削除などの通常操作は3秒以内に応答。

### データ量の対応

* 最大数百種類の食材データを管理。

# 非機能要件：セキュリティ {#非機能要件：セキュリティ}

### データ保護

ユーザーの食材情報や予算情報は暗号化して保存。

### APIセキュリティ

AWS API Gatewayを使用して認証し、不正アクセスを防止。

# 非機能要件：移行性 {#非機能要件：移行性}

### スケーラビリティ

将来的にはモバイルアプリに移行しやすい構成を採用（React Native）。

### データ移行

H2からPostgreSQLへのデータマイグレーションを容易にするツールや手順を検討。

# 非機能要件：プロジェクト上の留意事項 {#非機能要件：プロジェクト上の留意事項}

コスト管理

* AWSの無料枠を最大限利用し、開発コストを削減。

開発効率

* 開発を短期間で完了させるため、ReactやAWS Amplifyなどの効率的なツールを採用。

ユーザー目線の設計

* 初心者にも使いやすいUI/UXデザインを重視。

# 参考資料

* Minimumskills. (2023). **「要件定義書」を作成してみる**. Qiita. [https://qiita.com/minimumskills/items/f9589953d48118d9f71f](https://qiita.com/minimumskills/items/f9589953d48118d9f71f)  
* OpenAI. (2025). **ChatGPT (バージョン4)**. OpenAI. [https://openai.com/chatgpt](https://openai.com/chatgpt)  
* Kojiro30. (2023). **自作WebサービスとLINEを超簡単に連携させる！！【LINE Notifyのご紹介】**. Qiita.[https://qiita.com/kojiro30/items/e1272eee92a02f383c1f](https://qiita.com/kojiro30/items/e1272eee92a02f383c1f)

# プロジェクトスケジュール {#プロジェクトスケジュール}

プロジェクトスケジュールには以下のマイルストーンを設定する:

* 要件定義完了日: 〇〇年〇月〇日  
* 基本設計完了日: 〇〇年〇月〇日  
* 開発完了日: 〇〇年〇月〇日  
* テスト完了日: 〇〇年〇月〇日」

# プロジェクト体制 {#プロジェクト体制}

# メモ書き {#メモ書き}

通知の仕組み案  
ラインで通知送る  
AWS Amplify → API Gateway → Lambda→ LINE Notify   
１～５人くらいならワンチャン無料枠で行ける？？？？

AWS Amplify → API Gateway → Lambda を使って LINE Notify に通知を送るシステムを構築する場合、各サービスの無料利用枠について以下のように説明できます。**無料で運用できるかどうかは、利用規模に大きく依存**します。

---

### **1\. AWS Amplify**

* **無料利用枠**:  
  * AWS Amplify Hosting: 月1,000ビルド分の無料枠。  
  * 静的ウェブサイトホスティングの利用が中心の場合、この無料枠でほぼ十分です。  
* **追加費用**:  
  * 利用量が増えると課金が発生しますが、簡単なアプリ程度であれば無料枠内で収まる可能性が高いです。

---

### **2\. API Gateway**

* **無料利用枠**:  
  * HTTP API または REST API のどちらでも、**月100万回のAPIリクエスト無料**。  
* **追加費用**:  
  * 100万回を超えた場合、HTTP APIは$1/1百万リクエスト、REST APIは$3.50/1百万リクエスト（リージョンによる）。  
  * 個人用途でLINE Notify通知のトリガー程度なら、無料枠内に収まることがほとんど。

---

### **3\. AWS Lambda**

* **無料利用枠**:  
  * **毎月100万リクエスト無料**。  
  * 計算時間（compute time）は40万GB-秒（リクエスト数に基づく計算量の合計）が無料。  
* **追加費用**:  
  * リクエスト数や計算時間が超過すると課金されますが、LINE通知程度の簡単な処理であれば無料枠内で十分。

---

### **4\. LINE Notify**

* **無料**:  
  * LINE Notify自体は無料で利用可能。  
  * トークンを発行し、HTTPリクエストを送信するだけなので課金は発生しません。

---

### **結論**

* **無料で可能かどうか**:  
  * 小規模（例えば1日数回程度の通知）であれば、上記のAWS無料利用枠を利用して**完全無料で運用可能**です。  
  * ただし、利用規模が拡大するとAPI GatewayやLambdaの無料枠を超える可能性があります。  
* **注意点**:  
  * AWS無料枠は登録から12か月間のみ有効です（一部サービスは期間制限なし）。  
  * 12か月を過ぎると、上記の利用量に応じて課金されます。  
  * 無料枠を超える場合でも、数百リクエスト/月程度の利用なら微小なコストで済みます。

---

### **コスト見積もり例**

1. **月に30回の通知**:  
   * Amplify Hosting: 無料。  
   * API Gateway: 月30リクエスト → 無料枠内。  
   * Lambda: 月30リクエストで軽量な処理 → 無料枠内。  
   * LINE Notify: 無料。  
   * **合計コスト: $0**  
2. **月に10,000回の通知**:  
   * Amplify Hosting: 無料。  
   * API Gateway: 10,000リクエスト → 無料枠内。  
   * Lambda: 10,000リクエスト → 無料枠内。  
   * LINE Notify: 無料。  
   * **合計コスト: $0**

**12か月以降**の状況を考える場合や、無料枠を超える可能性を確認するために、AWSのコストエクスプローラーなどを利用してモニタリングするのがおすすめです！

[^1]:  ユーザーは通知のタイミング（例: 1日前、3日前）や通知内容（例: 賞味期限、消費期限の差異）をアプリ内で設定できるようにする。

[image1]: <data:image/png;base64,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>