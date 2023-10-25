# **OHDSI Tool Documents**

## **Usagi**  
```
Usagi は、独自に定義した各種項目（薬品、病名など）を CONCEPT テーブルへマッピングするための補助ツールです。  
```
- [セットアップ手順](./Usagi_setup.md)
- [操作手順](./Usagi_operation.md)

<br>

---
## **WhiteRabbit & Rabbit-in-a-Hat**  
```
OMOP CDM の各リソースへマッピング支援するのが、Rabbit-in-a-Hat です。  
Rabbit-in-a-Hat でマッピング作業を進めるために、White Rabbit では入力データを Rabbi-in-a-Hat で取り込み可能な形式に加工します。  
```
- [セットアップ手順](./WhiteRabbit_setup.md)
- [操作手順](./WhiteRabbit_operation.md)

<br>

---
## **Atlas**  
```
Atlas は、OMOP 共通データモデル（CDM）に変換され、標準化された観測データに対して科学的分析を実施するためのオープンソースソフトウェアツールです。  
患者コホートの定義、分析設計の選択、パラメータの設定、データに対する分析手法の実行を可能にします。  
Eunomia のテストデータは、Atlas の各分析の検証に役立ちます。
```
- [セットアップ手順](./Atlas_setup.md)
- [Eunomia テストデータのセットアップ手順](./Eunomia_setup.md)
- [操作手順 ～Cohort Pathways 編～](./Atlas_operation_CohortPathways.md)
- [操作手順 ～Characterizations 編～](./Atlas_operation_Characterizations.md)
- [操作手順 ～Incidence Rates 編～](./Atlas_operation_IncidenceRates.md)
- [機能調査資料](./Atlas_functional_survey.md)
- [アプリケーションのバージョン](./Verified_Version.md)
- [プロキシ設定手順](./Proxy_setting.md)
※プロキシサーバによりインストールの通信がブロックされる場合は、設定が必要です

<br>

---
## **HADES**  
```
母集団の特性評価、母集団レベルの因果効果の推定、患者レベルの予測など、大規模な分析のための20個のオープンソース R パッケージのセットです。  
```
- [セットアップ手順](./HADES_setup.md)
- [機能概要](.\/HADES_function.md)

<br>

---
各ツールのドキュメントにおいて、GitHub Issues で課題の管理を行っています。  
https://github.com/RWD-data-environment-in-Hospital/Documents/issues

[GitHub Issues について](./GitHub_Issues.md)

<br>
<br>
本資料は「医療技術実用化総合促進事業 Real World Evidence 創出のための取組み（通称：臨中ネット）」の支援を受けて作成されました。

- [作成協力者](./HADES_setup.md)