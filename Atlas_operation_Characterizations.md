# **Atlas 操作手順 ～Characterizations～**

### **目次**
1　本手順について  
2　Characterizations 操作の流れ  
3　Concept Sets の作成  
4　Cohort Definitions の作成  
5　Feature Analyses （特徴分析）の作成  
6　Characterizations （特性評価）  
7　補足資料  

<br>

---
# **1　本手順について**
Atlas の Characterizations 操作手順について説明します。  
本操作手順は、以下の Atlas 動作環境が整備されていることを前提としています。  

- Windows10（64 ビット）  
- Java 8 Java Development Kit (JDK)  
- Atlas セットアップ（「Atlas セットアップ手順」参照）  
- Eunomia テストデータのセットアップ（「Atlas 操作手順 Eunomia のテストデータセットアップについて」参照）  

<br>

---
# **2　Characterizations 操作の流れ**
本操作手順書では、以下に示す Characterizations を用いた分析を対象にした手順を記載しています。  

![](./Files/Atlas_4/image/image0.png)

本書では、Eunomia のテストデータを使用して Atlas の Characterizations による分析を実施します。  
Characterizations による分析の操作手順では、次の事例を取り上げて説明します。  
- 「胆嚢摘出手術」と「腹腔鏡下 胆嚢摘出術」の術式を母集団とし、該当の手術を受けた患者における診断された病名、処方された薬剤、受けた検査項目の人数と発生率を統計します。  

<br>

Characterizations による分析は、上記事例に従い、以下のテストデータを用いて説明します。  
1）Cohort Definitions - 調査項目（母集団）  
- ＜術式＞  
  - Laparoscopic cholecystectomy（腹腔鏡下 胆嚢摘出術）  
  - Cholecystectomy（胆嚢摘出術）  

<br>

2）Feature analyses - 分析項目（レポート）  
- ＜診断された病名＞  
  - Gallstone（胆石）  
  - Acute cholecystitis（急性胆嚢炎）  

<br>

- ＜処方された薬剤＞  
  - 1 ML Morphine Sulfate 5 MG/ML Injection (1 ML モルヒネ硫酸塩 5 MG/ML 注射)  
  - 100 ML Propofol 10 MG/ML Injection (100 ML プロポフォール 10 MG/ML 注射)  
  - 2 ML Ondansetron 2 MG/ML Injection (2 ML オンダンセトロン 2 MG/ML インジェクション)  
  - Acetaminophen 160 MG Oral Tablet (アセトアミノフェン 160 MG 経口錠剤)  
  - heparin (ヘパリン)  
  - Isoflurane 999 MG/ML Inhalant Solution (イソフルラン 999 MG/ML 吸入剤溶液)  
  - Meperidine Hydrochloride 50 MG Oral Tablet (メペリジン塩酸塩50 MG 経口錠剤)  
  - Midazolam 1 MG/ML Injectable Solution (ミダゾラム 1 MG/ML 注射液)  
  - Piperacillin 4000 MG/tazobactam 500 MG Injection (ピペラシリン 4000 MG/タゾバクタム 500 MG 注射)  
  - remifentanil (レミフェンタニル)  
  - rocuronium bromide 10 MG/ML Injectable Solution (臭化ロクロニウム 10 MG/ML 注射液)  
  - sevoflurane 1000 MG/ML Inhalant Solution (セボフルラン 1000 MG/ML 吸入剤溶液)  
  - Sodium Chloride 9 MG/ML Injectable Solution (塩化ナトリウム 9 MG/ML 注射液)  
  - Fentanyl (スフェンタニル)  

  <br>

- ＜受けた検査＞  
  - Globulin [Mass/volume] in Serum by calculation（血清中のグロブリン [質量/体積] ）  
  - Hematocrit（ヘマトクリット（血中赤血球容積））  
  - Hemoglobin（ヘモグロビン（Hb））

<br>

---
# **3　Concept Sets の作成**
「Concept Sets」では、分析で使用する独自のリストを作成します。  
分析対象の用語のセットを特定して作成し、再利用することも可能です。  
コンセプトセットは、以下の属性を持つコンセプトのリストで構成します。  

- Exclude：  
選択したコンセプト（Descendantsにチェックを入れた場合はその派生も含めて）をコンセプトセットから除外する。  

- Descendants：  
選択したコンセプトだけでなく、その派生のコンセプトについても考慮する。  

- Mapped：  
非標準のコンセプトを検索可能にする。  

<br>

Characterizations による分析では、事前に「Cohort Definitions - 調査項目」と「Feature analyses - 分析項目」の詳細項目を Concept Sets に登録します。  
前章に取り上げた＜術式＞、＜病名＞、＜薬剤＞および＜検査項目＞は、すべて登録対象になります。  

<br>

以下で作成方法を示します。  
本手順では、「Cholecystectomy（胆嚢摘出術）」のコンセプトセットの作成を例として取り上げます。  

<br>

Atlas 画面左の「Concept Sets」をクリックすると、Atlas プラットフォーム内ですでに作成されたコンセプトセットが表示されます。  

![](./Files/Atlas_4/image/image1.png)

<br>

新たにコンセプトセットを作成するので、画面右の「New Concept Set」をクリックして作成画面に遷移します。  

![](./Files/Atlas_4/image/image118.png)

<br>

画面上部に新規に作成するコンセプトセットの名前を入力します。  

![](./Files/Atlas_4/image/image2.png)

<br>

「Concept Set Expression」タブの「Add Concepts」をクリックすると Search 画面に遷移します。  

![](./Files/Atlas_4/image/image3.jpeg)

<br>

Search 画面では、キーワードやコンセプトIDを入力することで対象とするコンセプトを探すことができます。  
下記のコンセプトを検索し、Concept Sets へ登録します。  

|Id|Code|Name|Class|Domain|Vocabulary|
|:---|:---|:---|:---|:---|:---|
|4242997|38102005|Cholecystectomy|Procedure|Procedure|SNOMED|

<br>

➀Search 画面のテキスト入力欄へ  「Cholecystectomy」 と入力します。  
②検索ボタンをクリックすると、対象のリストが表示されます。  
③表示されたリストから「4242997：Cholecystectomy」にチェックを入れます。  
④Select Concept Set に「Cholecystectomy」が選択されていることを確認します。  
⑤Descendants にチェックを入れます。  
⑥Add To Concept Set をクリックします。(ConceptSetsに組み込まれます)  

![](./Files/Atlas_4/image/image120.png)

<br>

左メニューの「Concept Sets」をクリックします。  
「Cholecystectomy」セットにコンセプトが追加され、独自のコンセプトセットが形成されたことを確認します。  

![](./Files/Atlas_4/image/image121.png)

<br>

画面右上の緑の保存ボタンをクリックすると、「Concept Sets」のトップ画面の一覧に作成したコンセプトセットが追加されます。  
※派生するコンセプトも分析に含める想定のため、「Descendants」を有効にしています。  
（各コンセプトについて、「Exclude」、「Descendants」、「Mapped」をこの画面からも設定できます）  

![](./Files/Atlas_4/image/image122.png)

<br>

以上でコンセプトセット「Cholecystectomy」の作成が完了しました。  
×ボタンをクリックして、コンセプトセット「Gastrointestinal hemorrhage」の画面を閉じます。  

![](./Files/Atlas_4/image/image123.png)

<br>

同様の操作で、以下のコンセプトセットについても作成します。  

＜術式＞
- Laparoscopic cholecystectomy

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|4163971|45595009|Laparoscopic cholecystectomy|Procedure|Standard||✓||

<br>
<br>

＜病名＞  
- Gallstone

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|196456|235919008|Gallstone|Condition|Standard||✓||

<br>

- Acute cholecystitis

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|198809|65275009|Acute cholecystitis|Condition|Standard||✓||

<br>
<br>

＜薬剤＞  
- 1 ML Morphine Sulfate 5 MG/ML Injection

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|35605858|1732136|1 ML Morphine Sulfate 5 MG/ML|Drug|Standard||✓||

<br>

- 2 ML Ondansetron 2 MG/ML Injection

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|35605482|1740467|2 ML Ondansetron 2 MG/ML Injection|Drug|Standard||✓||

<br>

- 100 ML Propofol 10 MG/ML Injection

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|40220386|1808217|100 ML Propofol 10 MG/ML Injection|Drug|Standard||✓||

<br>

- Acetaminophen 160 MG Oral Tablet

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|1127078|282464|Acetaminophen|160 MG Oral Tablet|Drug|Standard||✓||

<br>

- heparin

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|1367571|5224|heparin|Drug|Standard||✓||

<br>

- Isoflurane 999 MG/ML Inhalant Solution

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|782047|542347|Isoflurane 999 MG/ML Inhalant Solution|Drug|Standard||✓||

<br>

- Meperidine Hydrochloride 50 MG Oral Tablet

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|40165015|861467|Meperidine Hydrochloride 50 MG Oral Tablet|Drug|Standard||✓||

<br>

- Midazolam 1 MG/ML Injectable Solution

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|19078924|311700|Midazolam 1 MG/ML Injectable Solution|Drug|Standard||✓||

<br>

- Piperacillin 4000 MG/tazobactam 500 MG

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|46275444|1659149|Piperacillin 4000 MG/tazobactam 500 MG|Drug|Standard||✓||

<br>

- remifentanil

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|19016749|73032|remifentanil|Drug|Standard||✓||

<br>

- rocuronium bromide 10 MG/ML Injectable Solution

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|42707627|1234995|rocuronium bromide 10 MG/ML Injectable Solution|Drug|Standard||✓||

<br>

- sevoflurane 1000 MG/ML Inhalant Solution

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|19023398|200243|sevoflurane 1000 MG/ML Inhalant Solution|Drug|Standard||✓||

<br>

- Sodium Chloride 9 MG/ML Injectable Solution

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|19079524|313002|Sodium Chloride 9 MG/ML Injectable Solution|Drug|Standard||✓||

<br>

- Sufentanil

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|19078219|56795|Sufentanil|Drug|Standard||✓||

<br>
<br>

＜検査項目＞  
- Globulin [Mass/volume] in Serum by calculation

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|3027970|10834-0|Globulin [Mass/volume] in Serum by calculation|Measurement|Standard||✓||

<br>

- Hematocrit

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|3009542|20570-8|Hematocrit|Measurement|Standard||✓||

<br>

- Hemoglobin

|Concept Id|Concept Code|Concept Name|Domain|Standard Concept Caption|Exclude|Descendants|Mapped|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|3000963|718-7|Hemoglobin|Measurement|Standard||✓||

<br>

以上でコンセプトセットの作成は完了です。  

<br>

---
# **4　Cohort Definitionsの作成**

コホートとは、「一定期間1つ以上の基準を満たす一連の人物」と定義され、Cohort Definitions はコホートを構築する機能を持ちます。  
作成されたコホートは、その後の Characterizations 機能での分析における母集団設定に使用されます。

コホート定義では、「Cohort entry events（コホート開始イベント）」、「Inclusion Criteria（包含基準）」、「Cohort exit event（コホート終了イベント）」を設定する構成となっており、各項目の詳細を以下に記載しています。  

- コホート開始イベント：  
共通データモデルに記録された任意のイベント（薬物曝露、疾病、検査など）を設定し、人々がコホートに入る時間を定義するものです。  
例えば、発生時の年齢、最初の診断・手順、開始日と終了日の指定、などを定義します。

- 包含基準：  
開始イベントで定義された人々をさらに絞り込むためのイベントを設定します。  
予選コホートは、すべての包括基準を満たす最初のイベントコホート内のすべての人々を指します。  

- コホート終了イベント：  
人々がコホートメンバーシップの資格を失うイベントのことです。  
例えば、観察期間の終了、最初の開始イベントに対する固定時間間隔、一連の関連する観察の最後のイベント（持続的な薬物曝露）、など複数の方法で定義可能です。  
コホートの出口戦略は、人が異なる時間間隔の間に複数回コホートに所属できるかどうかに影響します。  

<br>

ここでは、「腹腔鏡下 胆嚢摘出術と胆嚢摘出術の手術を受けている患者」を例に Cohort Definitions の使用方法を説明します。  

<br>

以下の２つの術式についてのコンセプトセットを登録します。  
- Laparoscopic cholecystectomy
- Cholecystectomy

<br>

Atlas 画面の左タブから「Cohort Definitions」画面を開くと、Atlas プラットフォーム内ですでに作成されたコホートが表示されます。  
コホートを新規作成するので、「New Cohort」をクリックします。  

![](./Files/Atlas_4/image/image119.png)

<br>

コホート作成画面が表示されます。  
画面上部にコホート名を入力する欄があるので、「Cholecystectomy Definition」と入力します。  

![](./Files/Atlas_4/image/image9.png)

<br>

初めに、コホートエントリーイベントを設定していきます。  

![](./Files/Atlas_4/image/image10.jpeg)

<br>

「Cohort Entry Events」欄右側の「+Add Initial Event...」をクリックして、「Add Procedure Occurrence」を選択します。  

![](./Files/Atlas_4/image/image11.png)

<br>

「Any Procedure」で対象とする手術のコンセプトセットの選択が必要になります。  
「Any Procedure」の▼をクリックし、「Import Concept Set」を開くと作成されているコンセプトセットの一覧が表示されるので、「Cholecystectomy」をクリックして選択します。  
※もし、誤ったコンセプトセットをインポートしてしまった場合は、「Clear Concept Set」を選択することで、インポートを解除することが出来ます  

![](./Files/Atlas_4/image/image12.png)

<br>

手術前後の観察期間については、特に指定しないのでデフォルトのままにします。  
※「0 days」の選択で全期間のデータが対象となります  
対象イベントは「all events」を選択します。  

以上で、術式Cholecystectomyの「Cohort Entry Events」の設定は完了です。  

<br>

次に、「Inclusion Criteria」欄の設定を実施します。  

![](./Files/Atlas_4/image/image13.png)

<br>

緑色ボタンの「New inclusion criteria」をクリックし、横の空欄内に包含基準名として「Cholecystectomy」を入力します。  
左側に入力した名前が反映されます。  

![](./Files/Atlas_4/image/image14.png)

<br>

術式の診断を基準としているので、「+Add Initial Event...」から「Add Procedure Occurrence」を選択します。  

![](./Files/Atlas_4/image/image15.png)

<br>

選択後、欄内に図のような詳細設定画面が表示されます。  

![](./Files/Atlas_4/image/image16.jpeg)

