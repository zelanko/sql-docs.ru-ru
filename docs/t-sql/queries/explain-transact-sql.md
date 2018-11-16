---
title: EXPLAIN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: cef2b01c9b9d5147583cc4419fd105bd3e91503f
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701422"
---
# <a name="explain-transact-sql"></a>EXPLAIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает план запроса для инструкции [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] без выполнения инструкции. Используйте **EXPLAIN**, чтобы узнать, каким операциям потребуется перемещение данных, и определить предполагаемые затраты на операции запроса.  
  
 Дополнительные сведения о планах запросов см. в разделе "Основные сведения о планах запросов" в [!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  

```  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *SQL_statement*  
 Инструкция [!INCLUDE[DWsql](../../includes/dwsql-md.md)], в которой будет выполняться команда **EXPLAIN**. Аргумент *SQL_statement* может быть любой из следующих команд: **SELECT**, **INSERT**, **UPDATE**, **DELETE**, **CREATE TABLE AS SELECT**, **CREATE REMOTE TABLE**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **SHOWPLAN** на выполнение *SQL_statement*. См. раздел [Разрешения: GRANT, DENY, REVOKE (хранилище данных SQL Azure, Parallel Data Warehouse)](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемым значением выполнения команды **EXPLAIN** является XML-документ со структурой, показанной ниже. В этом XML-документе перечислены все операции в плане запроса для данного запроса. Каждая операция заключена в тег `<dsql_operation>`. Возвращаемое значение имеет тип **nvarchar(max)**.  
  
 Возвращенный план запроса показывает последовательные инструкции SQL. Выполняемый запрос может сопровождаться параллелизованными операциями, поэтому некоторые приведенные последовательные инструкции могут выполняться одновременно.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<dsql_query>  
  <sql>. . .</sql>  
  <params />  
  <dsql_operations>  
    <dsql_operation>  
     . . .      
    </dsql_operation>  
    [ . . . n ]  
  <dsql_operations>  
</dsql_query>  
```  
  
 XML-теги содержат приведенные ниже сведения.  
  
|XML-тег|Сводка, атрибуты и содержимое|  
|-------------|--------------------------------------|  
|\<dsql_query>|Элемент верхнего уровня или документа.|
|\<sql>|Отображает *SQL_statement*.|  
|\<params>|Этот тег в настоящее время не используется.|  
|\<dsql_operations>|Обобщает и содержит действия запроса, а также включает сведения о стоимости запроса. Также содержит все блоки `<dsql_operation>`. Этот тег содержит сведения о количестве для всего запроса.<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost* — общее предполагаемое время выполнения запроса (в мс).<br /><br /> *total_number_operations* — общее количество операций запроса. Операция, которая будет обрабатываться параллельно и выполняться на нескольких узлах, считается одной операцией.|  
|\<dsql_operation>|Описывает одну операцию в плане запроса. Тег \<dsql_operation> содержит тип операции, как атрибут:<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *operation_type* является одним из значений в [запросе данных (SQL Server PDW)](https://msdn.microsoft.com/3f4f5643-012a-4c36-b5ec-691c4bbe668c).<br /><br /> Содержимое в блоке `\<dsql_operation>` зависит от типа операции.<br /><br /> См. таблицу ниже.|  
  
|Тип операции|Содержимое|Пример|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE, DISTRIBUTE_REPLICATED_TABLE_MOVE, MASTER_TABLE_MOVE, PARTITION_MOVE, SHUFFLE_MOVE и TRIM_MOVE|Элемент `<operation_cost>` с этими атрибутами. Значения отражают только локальную операцию:<br /><br /> -   *cost* — стоимость локального оператора и отображение предполагаемого времени выполнения операции (в мс).<br />-   *accumulative_cost* — сумма всех операций в плане, включая суммарные значения для параллельных операций (в мс).<br />-   *average_rowsize* — предполагаемый средний размер строки (в байтах) строк, извлекаемых и передаваемых во время операции.<br />-   *output_rows* — количество выходных элементов (узлов) с отображением числа выходных строк.<br /><br /> `<location>`: узлы или распределения, в которых будет выполняться операция. Возможные варианты: Control, ComputeNode, AllComputeNodes, AllDistributions, SubsetDistributions, Distribution и SubsetNodes.<br /><br /> `<source_statement>`: исходные данные для перемещения в случайном порядке.<br /><br /> `<destination_table>`: внутренняя временная таблица, в которую будут перемещены данные.<br /><br /> `<shuffle_columns>`: (применимо только к операциям SHUFFLE_MOVE). Один или несколько столбцов, которые будут использоваться в качестве столбцов распределения для временной таблицы.|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`: см. `<operation_cost>` выше.<br /><br /> `<DestinationCatalog>`: целевой узел или узлы.<br /><br /> `<DestinationSchema>`: схема назначения в DestinationCatalog.<br /><br /> `<DestinationTableName>`: имя целевой таблицы или TableName.<br /><br /> `<DestinationDatasource>`: имя или сведения о подключении для целевого источника данных.<br /><br /> `<Username>` и `<Password>`: эти поля указывают, что для места назначения могут потребоваться имя пользователя и пароль.<br /><br /> `<BatchSize>`: размер пакета для операции копирования.<br /><br /> `<SelectStatement>`: инструкция Select, используемая для копирования.<br /><br /> `<distribution>`: распределение, где выполняется копирование.|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: исходная таблица для копирования.<br /><br /> `<destionation_table>`: целевая таблица для копирования.|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`: см. `<location>` выше.<br /><br /> `<sql_operation>`: определяет команду SQL, которая будет выполняться на узле.|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: каталог назначения.<br /><br /> `<DestinationSchema>`: схема назначения в DestinationCatalog.<br /><br /> `<DestinationTableName>`: имя целевой таблицы или TableName.<br /><br /> `<DestinationDatasource>`: имя целевого источника данных.<br /><br /> `<Username>` и `<Password>`: эти поля указывают, что для места назначения могут потребоваться имя пользователя и пароль.<br /><br /> `<CreateStatement>`: инструкция создания таблицы для целевой базы данных.|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: идентификатор для результирующего набора.|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: идентификатор для создаваемого объекта.|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **EXPLAIN** можно применять только к *оптимизируемым* запросам, которые представляют собой импортируемые или изменяемые запросы на основе результатов выполнения команды **EXPLAIN**. Поддерживаемые команды **EXPLAIN** приведены выше. При попытке использовать **EXPLAIN** с неподдерживаемым типом запроса возвращается ошибка или сам запрос.  
  
 **EXPLAIN** не поддерживается в пользовательской транзакции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано выполнение команды **EXPLAIN** в инструкции **SELECT** и выведен результат в формате XML.  
  
 **Отправка инструкции EXPLAIN**  
  
 В этом примере отправленная команда имеет вид:  
  
```  
-- Uses AdventureWorks  
  
EXPLAIN   
    SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
        CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
        G.StateProvinceName, T.SalesTerritoryGroup  
    FROM dbo.DimGeography AS G  
    JOIN dbo.DimSalesTerritory AS T  
        ON G.SalesTerritoryKey = T.SalesTerritoryKey  
    JOIN dbo.DimCustomer AS C  
        ON G.GeographyKey = C.GeographyKey  
    JOIN dbo.FactInternetSales AS FIS  
        ON C.CustomerKey = FIS.CustomerKey  
    WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
        AND Gender = 'F'  
    GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
    ORDER BY AVG(YearlyIncome) DESC;  
GO  
```  
  
 После выполнения инструкции с параметром **EXPLAIN** на вкладке сообщений находится одна строка с названием **explain**, которая начинается с XML-текста `\<?xml version="1.0" encoding="utf-8"?>`. Щелкните XML, чтобы полностью открыть текст в окне XML. Чтобы лучше понять следующие комментарии, необходимо включить отображение номеров строк в SSDT.  
  
#### <a name="to-turn-on-line-numbers"></a>Включение номеров строк  
  
1.  Пока на вкладке **explain** в вкладке SSDT отображаются выходные данные, выберите в меню **Сервис** пункт **Параметры**.  
  
2.  Разверните раздел **Текстовый редактор**, разверните **XML**, а затем щелкните **Общие**.  
  
3.  В области **Отображение** щелкните **Номера строк**.  
  
4.  Нажмите кнопку **ОК**.  
  
 **Пример выходных данных EXPLAIN**  
  
 Отображается следующий XML-результат выполнения команды **EXPLAIN** с включенными номерами строк:  
  
```  
1  \<?xml version="1.0" encoding="utf-8"?>  
2  <dsql_query>  
3    <sql>SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
4          CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
5          G.StateProvinceName, T.SalesTerritoryGroup  
6      FROM dbo.DimGeography AS G  
7      JOIN dbo.DimSalesTerritory AS T  
8          ON G.SalesTerritoryKey = T.SalesTerritoryKey  
9      JOIN dbo.DimCustomer AS C  
10          ON G.GeographyKey = C.GeographyKey  
11      JOIN dbo.FactInternetSales AS FIS  
12          ON C.CustomerKey = FIS.CustomerKey  
13      WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
14          AND Gender = 'F'  
15      GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
16      ORDER BY AVG(YearlyIncome) DESC</sql>  
17    <dsql_operations total_cost="0.926237696" total_number_operations="9">  
18      <dsql_operation operation_type="RND_ID">  
19        <identifier>TEMP_ID_16893</identifier>  
20      </dsql_operation>  
21      <dsql_operation operation_type="ON">  
22        <location permanent="false" distribution="AllComputeNodes" />  
23        <sql_operations>  
24          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16893] ([CustomerKey] INT NOT NULL, [GeographyKey] INT, [YearlyIncome] MONEY ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
25        </sql_operations>  
26      </dsql_operation>  
27      <dsql_operation operation_type="BROADCAST_MOVE">  
28        <operation_cost cost="0.121431552" accumulative_cost="0.121431552" average_rowsize="16" output_rows="31.6228" />  
29        <source_statement>SELECT [T1_1].[CustomerKey] AS [CustomerKey],  
30         [T1_1].[GeographyKey] AS [GeographyKey],  
31         [T1_1].[YearlyIncome] AS [YearlyIncome]  
32  FROM   (SELECT [T2_1].[CustomerKey] AS [CustomerKey],  
33                 [T2_1].[GeographyKey] AS [GeographyKey],  
34                 [T2_1].[YearlyIncome] AS [YearlyIncome]  
35          FROM   [AdventureWorksPDW2012].[dbo].[DimCustomer] AS T2_1  
36          WHERE  ([T2_1].[Gender] = CAST (N'F' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (1)) COLLATE Latin1_General_100_CI_AS_KS_WS)) AS T1_1</source_statement>  
37        <destination_table>[TEMP_ID_16893]</destination_table>  
38      </dsql_operation>  
39      <dsql_operation operation_type="RND_ID">  
40        <identifier>TEMP_ID_16894</identifier>  
41      </dsql_operation>  
42      <dsql_operation operation_type="ON">  
43        <location permanent="false" distribution="AllDistributions" />  
44        <sql_operations>  
45          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16894] ([StateProvinceName] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS, [SalesTerritoryGroup] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, [col] BIGINT, [col1] MONEY NOT NULL, [col2] BIGINT, [col3] MONEY NOT NULL ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
46        </sql_operations>  
47      </dsql_operation>  
48      <dsql_operation operation_type="SHUFFLE_MOVE">  
49        <operation_cost cost="0.804806144" accumulative_cost="0.926237696" average_rowsize="232" output_rows="108.406" />  
50        <source_statement>SELECT [T1_1].[StateProvinceName] AS [StateProvinceName],  
51         [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
52         [T1_1].[col2] AS [col],  
53         [T1_1].[col] AS [col1],  
54         [T1_1].[col3] AS [col2],  
55         [T1_1].[col1] AS [col3]  
56  FROM   (SELECT ISNULL([T2_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col],  
57                 ISNULL([T2_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col1],  
58                 [T2_1].[StateProvinceName] AS [StateProvinceName],  
59                 [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
60                 [T2_1].[col] AS [col2],  
61                 [T2_1].[col2] AS [col3]  
62          FROM   (SELECT   COUNT_BIG([T3_2].[YearlyIncome]) AS [col],  
63                           SUM([T3_2].[YearlyIncome]) AS [col1],  
64                           COUNT_BIG(CAST ((0) AS INT)) AS [col2],  
65                           SUM([T3_2].[SalesAmount]) AS [col3],  
66                           [T3_2].[StateProvinceName] AS [StateProvinceName],  
67                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
68                  FROM     (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
69                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
70                            FROM   [AdventureWorksPDW2012].[dbo].[DimSalesTerritory] AS T4_1  
71                            WHERE  (([T4_1].[SalesTerritoryGroup] = CAST (N'North America' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (13)) COLLATE Latin1_General_100_CI_AS_KS_WS)  
72                                    OR ([T4_1].[SalesTerritoryGroup] = CAST (N'Pacific' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (7)) COLLATE Latin1_General_100_CI_AS_KS_WS))) AS T3_1  
73                           INNER JOIN  
74                           (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
75                                   [T4_2].[YearlyIncome] AS [YearlyIncome],  
76                                   [T4_2].[SalesAmount] AS [SalesAmount],  
77                                   [T4_1].[StateProvinceName] AS [StateProvinceName]  
78                            FROM   [AdventureWorksPDW2012].[dbo].[DimGeography] AS T4_1  
79                                   INNER JOIN  
80                                   (SELECT [T5_2].[GeographyKey] AS [GeographyKey],  
81                                           [T5_2].[YearlyIncome] AS [YearlyIncome],  
82                                           [T5_1].[SalesAmount] AS [SalesAmount]  
83                                    FROM   [AdventureWorksPDW2012].[dbo].[FactInternetSales] AS T5_1  
84                                           INNER JOIN  
85                                           [tempdb].[dbo].[TEMP_ID_16893] AS T5_2  
86                                           ON ([T5_1].[CustomerKey] = [T5_2].[CustomerKey])) AS T4_2  
87                                   ON ([T4_2].[GeographyKey] = [T4_1].[GeographyKey])) AS T3_2  
88                           ON ([T3_1].[SalesTerritoryKey] = [T3_2].[SalesTerritoryKey])  
89                  GROUP BY [T3_2].[StateProvinceName], [T3_1].[SalesTerritoryGroup]) AS T2_1) AS T1_1</source_statement>  
90        <destination_table>[TEMP_ID_16894]</destination_table>  
91        <shuffle_columns>StateProvinceName;</shuffle_columns>  
92      </dsql_operation>  
93      <dsql_operation operation_type="ON">  
94        <location permanent="false" distribution="AllComputeNodes" />  
95        <sql_operations>  
96          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16893]</sql_operation>  
97        </sql_operations>  
98      </dsql_operation>  
99      <dsql_operation operation_type="RETURN">  
100        <location distribution="AllDistributions" />  
101        <select>SELECT   [T1_1].[col] AS [col],  
102           [T1_1].[col1] AS [col1],  
103           [T1_1].[StateProvinceName] AS [StateProvinceName],  
104           [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
105           [T1_1].[col2] AS [col2]  
106  FROM     (SELECT CONVERT (INT, [T2_1].[col], 0) AS [col],  
107                   CONVERT (INT, [T2_1].[col1], 0) AS [col1],  
108                   [T2_1].[StateProvinceName] AS [StateProvinceName],  
109                   [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
110                   [T2_1].[col] AS [col2]  
111            FROM   (SELECT CASE  
112                            WHEN ([T3_1].[col] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
113                            ELSE ([T3_1].[col1] / CONVERT (MONEY, [T3_1].[col], 0))  
114                           END AS [col],  
115                           CASE  
116                            WHEN ([T3_1].[col2] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
117                            ELSE ([T3_1].[col3] / CONVERT (MONEY, [T3_1].[col2], 0))  
118                           END AS [col1],  
119                           [T3_1].[StateProvinceName] AS [StateProvinceName],  
120                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
121                    FROM   (SELECT ISNULL([T4_1].[col], CONVERT (BIGINT, 0, 0)) AS [col],  
122                                   ISNULL([T4_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col1],  
123                                   ISNULL([T4_1].[col2], CONVERT (BIGINT, 0, 0)) AS [col2],  
124                                   ISNULL([T4_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col3],  
125                                   [T4_1].[StateProvinceName] AS [StateProvinceName],  
126                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
127                            FROM   (SELECT   SUM([T5_1].[col]) AS [col],  
128                                             SUM([T5_1].[col1]) AS [col1],  
129                                             SUM([T5_1].[col2]) AS [col2],  
130                                             SUM([T5_1].[col3]) AS [col3],  
131                                             [T5_1].[StateProvinceName] AS [StateProvinceName],  
132                                             [T5_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
133                                    FROM     [tempdb].[dbo].[TEMP_ID_16894] AS T5_1  
134                                    GROUP BY [T5_1].[StateProvinceName], [T5_1].[SalesTerritoryGroup]) AS T4_1) AS T3_1) AS T2_1) AS T1_1  
135  ORDER BY [T1_1].[col2] DESC</select>  
136      </dsql_operation>  
137      <dsql_operation operation_type="ON">  
138        <location permanent="false" distribution="AllDistributions" />  
139        <sql_operations>  
140          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16894]</sql_operation>  
141        </sql_operations>  
142      </dsql_operation>  
143    </dsql_operations>  
144  </dsql_query>  
  
```  
  
 **Значение выходных данных EXPLAIN**  
  
 В приведенных выше выходных данных содержатся 144 пронумерованные строки. Ваши выходные данные этого запроса могут немного отличаться. Далее приводится описание важных разделов.  
  
-   Строки 3–16 содержат описание анализируемого запроса.  
  
-   Строка 17 указывает, что общее число операций будет равно 9. Начало каждой операции можно найти, выполнив поиск слов **dsql_operation**.  
  
-   Строка 18 запускает операцию 1. Строки 18 и 19 указывают, что операция **RND_ID** создаст случайный идентификационный номер, который будет использоваться для описания объекта. В примере выходных данных выше описывается объект **TEMP_ID_16893**. Ваш номер будет другим.  
  
-   Строка 20 запускает операцию 2. Строки 21–25: на всех вычислительных узлах создать временную таблицу с именем **TEMP_ID_16893**.  
  
-   Строка 26 запускает операцию 3. Строки 27–37: переместить данные в объект **TEMP_ID_16893** с помощью широковещательного перемещения. Указывается запрос, отправляемый на каждый вычислительный узел. Строка 37 указывает, что целевой таблицей является **TEMP_ID_16893**.  
  
-   Строка 38 запускает операцию 4. Строки 39–40: создать случайный идентификатор таблицы. **TEMP_ID_16894** — номер идентификатора в предыдущем примере. Ваш номер будет другим.  
  
-   Строка 41 запускает операцию 5. Строки 42–46: на всех узлах создать временную таблицу с именем **TEMP_ID_16894**.  
  
-   Строка 47 запускает операцию 6. Строки 48–91: переместить данные из различных таблиц (включая **TEMP_ID_16893**) в таблицу **TEMP_ID_16894** с помощью операции перемещения в случайном порядке. Указывается запрос, отправляемый на каждый вычислительный узел. Строка 90 указывает, что целевой таблицей является **TEMP_ID_16894**. Строка 91 указывает столбцы.  
  
-   Строка 92 запускает операцию 7. Строки 93–97: на всех вычислительных узлах удалить временную таблицу **TEMP_ID_16893**.  
  
-   Строка 98 запускает операцию 8. Строки 99–135: возвратить результаты клиенту. Использует указанный запрос для получения результатов.  
  
-   Строка 136 запускает операцию 9. Строки 137–140: на всех узлах удалить временную таблицу **TEMP_ID_16894**.  
  
  

