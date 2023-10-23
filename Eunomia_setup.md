# **Eunomia テストデータのセットアップ**
※Eunomia テストデータのセットアップは、Atlas のセットアップが完了してから行ってください  

Eunomia は、Atlas のテストデータとして用意されたデータセットです。  
Eunomia を利用することにより、ATLAS の機能を実際に使いながら学ぶことができます。  
<br>
### **目次**
[1　Eunomia ライブラリのインストール](#1-eunomia-ライブラリのインストール)  
[2　Eunomia からデータのエクスポート](#2-eunomia-からデータのエクスポート)  
[3　データベースへのインポート](#3-データベースへのインポート)  
[4　Achilles の実行](#4-achilles-の実行)  

<br>

---
# **1　Eunomia ライブラリのインストール**
以下の手順に従い、インポートするデータを Eunomia からエクスポートします。  
まず、エクスポートするテストデータを格納するフォルダを作成しておきます。  

![](./Files/Atlas_3/image/image1.png)

<br>

※以降の記述は「D:\tmp\output」フォルダを作成した前提の内容となっています。  

続いて R コンソールを起動し、以下のコマンドを入力します。  
```
> install.packages("remotes")
```
![](./Files/Atlas_3/image/image83.png)

<br>

コマンド実行後、下記のメッセージが表示された場合、「はい」をクリックします。

![](./Files/Atlas_3/image/image73.png)
![](./Files/Atlas_3/image/image74.png)

<br>

CRAN ミラーサイトは、「0-Cloud [https]」を選択します。

![](./Files/Atlas_3/image/image75.png)

<br>

remotes パッケージのインストールが完了すると、下図のメッセージが表示されます。

![](./Files/Atlas_3/image/image84.png)


<br>

続いて下記のコマンドを実行し、「1: All」を選択します。

```
> remotes::install_github("ohdsi/Eunomia")
```

![](./Files/Atlas_3/image/image85.png)

<br>

下記のメッセージが表示されるので、「はい」をクリックします。  

![](./Files/Atlas_3/image/image87.png)

<br>

Eunomia パッケージのインストールが完了すると、下図のメッセージが表示されます。

![](./Files/Atlas_3/image/image86.png)

<br>

---
# **2　Eunomia からデータのエクスポート**

インストールされた Eunomia を読み込みます。  
以下のコマンドを入力します。  

```
> library(Eunomia)
```

![](./Files/Atlas_3/image/image80.png)

<br>

Eunomia を D:\tmp\output へエクスポートします。  
以下のコマンドを入力します。  

```
> folder <- "D:\\tmp\\output"
> exportToCsv(folder)
```

![](./Files/Atlas_3/image/image81.png)

<br>

下図のメッセージが表示されたらエクスポートは完了です。  

![](./Files/Atlas_3/image/image82.png)

<br>

作成したフォルダを表示し、エクスポートしたデータが格納されている事を確認します。  

![](./Files/Atlas_3/image/image5.png)

<br>

---
# **3　データベースへのインポート**
インポートを始める前に、エクスポートしたデータの内容を一部修正します。  

- concept_ancestor.csv  
ファイルを開き「3.6e+07」を「36000000」に、「3.7e+07」を「37000000」に置き換えます。  

- drug_exposure.csv  
ファイルをエクセルで開きＡ列（DRUG_EXPOSURE_ID）の内容を１からの連番に置き換えます。  

- measurement.csv  
ファイルをエクセルで開きＡ列（MEASUREMENT_ID）の内容を１からの連番に置き換えます。  

- observation.csv  
ファイルをエクセルで開きＡ列（OBSERVATION_ID）の内容を１からの連番に置き換えます。  
ファイルの修正が完了したら、以下の手順に従い Eunomia からエクスポートしたデータをインポートします。  

psql を起動し、データベース「OHDSI」へ接続します。  
コマンドプロンプトを起動し以下のコマンドを入力します。  
```
psql -U ohdsi_admin_user -d OHDSI
```

![](./Files/Atlas_3/image/image6.png)  
※パスワードはセットアップ時に設定したパスワードを入力します。  

データベースへ接続したら、参照スキーマを設定します。  
```
# set search_path to "cdmv5";
```

![](./Files/Atlas_3/image/image7.png)

<br>

以下のコマンドを入力し、データをインポートします。  
```
# \copy CDM_SOURCE from 'D:\\tmp\output\\CDM_SOURCE.csv' with delimiter ',' csv header
```

![](./Files/Atlas_3/image/image8.png)

<br>

実行が成功すると、インポートした件数が表示されます。  

![](./Files/Atlas_3/image/image9.png)

<br>

同様に以下のコマンドを入力して、データをインポートします。  

```
# \copy CONCEPT from 'D:\\tmp\output\\CONCEPT.csv' with delimiter ',' csv header
# \copy CONCEPT_ANCESTOR from 'D:\\tmp\output\\CONCEPT_ANCESTOR.csv' with delimiter ',' csv header
# \copy CONCEPT_RELATIONSHIP from 'D:\\tmp\output\\CONCEPT_RELATIONSHIP.csv' with delimiter ',' csv header
# \copy CONCEPT_SYNONYM from 'D:\\tmp\output\\CONCEPT_SYNONYM.csv' with delimiter ',' csv header
# \copy CONDITION_ERA from 'D:\\tmp\output\\CONDITION_ERA.csv' with delimiter ',' csv header
# \copy CONDITION_OCCURRENCE from 'D:\\tmp\output\\CONDITION_OCCURRENCE.csv' with delimiter ',' csv header
# \copy DOMAIN from 'D:\\tmp\output\\DOMAIN.csv' with delimiter ',' csv header
# \copy DRUG_ERA from 'D:\\tmp\output\\DRUG_ERA.csv' with delimiter ',' csv header
# \copy DRUG_EXPOSURE from 'D:\\tmp\output\\DRUG_EXPOSURE.csv' with delimiter ',' csv header
# \copy MEASUREMENT from 'D:\\tmp\output\\MEASUREMENT.csv' with delimiter ',' csv header
# \copy OBSERVATION from 'D:\\tmp\output\\OBSERVATION.csv' with delimiter ',' csv header
# \copy OBSERVATION_PERIOD from 'D:\\tmp\output\\OBSERVATION_PERIOD.csv' with delimiter ',' csv header
# \copy PERSON from 'D:\\tmp\output\\PERSON.csv' with delimiter ',' csv header
# \copy PROCEDURE_OCCURRENCE from 'D:\\tmp\output\\PROCEDURE_OCCURRENCE.csv' with delimiter ',' csv header
# \copy RELATIONSHIP from 'D:\\tmp\output\\RELATIONSHIP.csv' with delimiter ',' csv header
# \copy VISIT_OCCURRENCE from 'D:\\tmp\output\\VISIT_OCCURRENCE.csv' with delimiter ',' csv header
# \copy VOCABULARY from 'D:\\tmp\output\\VOCABULARY.csv' with delimiter ',' csv header FORCE NOT NULL vocabulary_version,vocabulary_reference
```

性別 CONCEPT の登録コマンドを実行します。  
```
# insert into cdmv5.concept values (8532,'FEMALE','Gender','Gender','Gender','S','F','1900-01-01','2099-12-31',NULL);
# insert into cdmv5.concept values (8507,'MALE','Gender','Gender','Gender','S','M','1900-01-01','2099-12-31',NULL);
```
以上でデータセットアップは完了です。

<br>

---
# **4　Achilles の実行**
Achilles は、Atlas 内で Data Source で表示されるデータの分析とレポート提供を実行しているツールです。  
Data Source 機能を使用するために Achilles の実行が必要となります。（Data Source の機能については、「Atlas 機能調査補足資料」を参照してください）  
データベースにデータをインポートした際や、登録されているデータを変更した場合に、Achilles を実行してください。  

R コンソールを起動し、以下のコマンドを入力し、Achilles を実行します。  
```
> library(Achilles)
```

![](./Files/Atlas_3/image/image10.png)

<br>

```
> Sys.setenv("DATABASECONNECTOR_JAR_FOLDER"="C:\\tomcat\\webapps\\WebAPI\\WEB-INF\\lib")
```

![](./Files/Atlas_3/image/image11.png)

<br>

```
> connectionDetails <- createConnectionDetails(
dbms="postgresql",
server="127.0.0.1/OHDSI",
user="ohdsi_app_user",
password="設定したパスワード",
port="5432")
```

![](./Files/Atlas_3/image/image12.png)

<br>

```
> achilles(
connectionDetails,
cdmDatabaseSchema="cdmv5",
resultsDatabaseSchema="webapi",
vocabDatabaseSchema="cdmv5",
numThreads=1,
sourceName="CDM V5 Database",
cdmVersion="5.3.1",
optimizeAtlasCache=TRUE)
```

![](./Files/Atlas_3/image/image13.png)

<br>

下記のメッセージが表示されたら実行完了です。

![](./Files/Atlas_3/image/image14.png)

以上で Achilles の実行は完了です。