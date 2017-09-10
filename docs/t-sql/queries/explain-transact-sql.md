---
title: "ОБЪЯСНЯЕТСЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b83d9a72ce1adbb37a80da8bfd52824b02fa16b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="explain-transact-sql"></a>ОБЪЯСНЯЕТСЯ (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает план запроса для [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] инструкцию без выполнения инструкции. Используйте **объяснение** Предварительный просмотр операции, которые потребуется перемещение данных и просматривать предполагаемых затрат операций запроса.  
  
 Дополнительные сведения о планах запросов см. в разделе «Основные сведения о планов запросов» в [!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  

```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *SQL_statement*  
 [!INCLUDE[DWsql](../../includes/dwsql-md.md)] Инструкции, на котором **объяснение** будет выполняться. *SQL_statement* может иметь любое из следующих команд: **ВЫБЕРИТЕ**, **вставить**, **обновление**, **удаление**,  **CREATE TABLE AS SELECT**, **создать УДАЛЕННУЮ ТАБЛИЦУ**.  
  
## <a name="permissions"></a>Permissions  
 Требуется **SHOWPLAN** разрешение и разрешение на выполнение *SQL_statement*. В разделе [разрешения: GRANT, DENY, REVOKE &#40; Хранилище данных Azure SQL, параллельное хранилище данных &#41; ](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение **объяснение** команда является XML-документа со структурой, показано ниже. Этот XML-документ перечислены все операции в плане запроса для данного запроса, заключенных в каждом `<dsql_operation>` тег. Возвращаемое значение имеет тип **nvarchar(max)**.  
  
 План запроса, возвращаемый описывается последовательные инструкции SQL; При выполнении запроса может содержать Параллелизованный операции некоторые показано последовательные инструкции могут выполняться одновременно.  
  
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
  
 XML-теги, содержащие эти сведения:  
  
|XML-тег|Сводка, атрибуты и содержимое|  
|-------------|--------------------------------------|  
|\<dsql_query >|Элемент верхнего уровня или документа.|
|\<SQL >|Эха *SQL_statement*.|  
|\<params >|Этот тег в настоящее время не используется.|  
|\<dsql_operations >|Обобщает и содержит действия запроса и включает сведения о стоимости для запроса. Также содержит все `<dsql_operation>` блоков. Этот тег содержит сведения о подсчете для всего запроса.<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost* общее предполагаемое время для запроса в мс.<br /><br /> *total_number_operations* — общее количество операций запроса. Операция, которая будет обработан параллельно и выполняются на нескольких узлах считается за одну операцию.|  
|\<dsql_operation >|Описывает одной операции в плане запроса. \<Dsql_operation > тег содержит тип операции, как атрибут:<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *operation_type* является одним из значений, найденных в [запрос данных (SQL Server PDW)](http://msdn.microsoft.com/en-us/3f4f5643-012a-4c36-b5ec-691c4bbe668c).<br /><br /> Содержимое в `\<dsql_operation>` блока зависит от типа операции.<br /><br /> См. в следующей таблице.|  
  
|Тип операции|Содержимое|Пример|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE, DISTRIBUTE_REPLICATED_TABLE_MOVE, MASTER_TABLE_MOVE, PARTITION_MOVE, SHUFFLE_MOVE и TRIM_MOVE|`<operation_cost>`элемент с этими атрибутами. Значения отражают только локальной операции:<br /><br /> -   *стоимость* стоимость локальный оператор и отображает предполагаемое время для запуска в миллисекундах операции.<br />-   *accumulative_cost* представляет сумму всех операций, которые видят в плане, включая суммарные значения для параллельных операций в мс.<br />-   *average_rowsize* имеет предполагаемый Средний размер строки (в байтах) строк извлекается и передается во время операции.<br />-   *output_rows* элементов выходных данных (узел) и отображает число выходных строк.<br /><br /> `<location>`: Узлов или распределения, в которых будет выполняться операция. Параметры являются: «Элемент управления», «ComputeNode», «AllComputeNodes», «AllDistributions», «SubsetDistributions», «Распространение» и «SubsetNodes».<br /><br /> `<source_statement>`: Переместить исходные данные для смещения.<br /><br /> `<destination_table>`: Внутренняя временной таблицы данные переносятся в.<br /><br /> `<shuffle_columns>`: (Применимо только к операциям SHUFFLE_MOVE). Один или несколько столбцов, которые будут использоваться в качестве столбцов распределения для временной таблицы.|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`: Просмотреть `<operation_cost>` выше.<br /><br /> `<DestinationCatalog>`: Целевой узел или узлы.<br /><br /> `<DestinationSchema>`: Схеме назначения в DestinationCatalog.<br /><br /> `<DestinationTableName>`: Имя целевой таблицы или «TableName».<br /><br /> `<DestinationDatasource>`: Имя или подключения сведения для источника данных назначения.<br /><br /> `<Username>`и `<Password>`: эти поля указывают, что имя пользователя и пароль для назначения может потребоваться.<br /><br /> `<BatchSize>`: Размер пакета для операции копирования.<br /><br /> `<SelectStatement>`: Инструкция select используется для выполнения копирования.<br /><br /> `<distribution>`: Распределение, где выполняется копирование.|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: Исходная таблица для операции.<br /><br /> `<destionation_table>`: Целевая таблица для операции.|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`: Просмотреть `<location>` выше.<br /><br /> `<sql_operation>`: Идентифицирует команду SQL, который будет выполняться на узле.|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: Конечный каталог.<br /><br /> `<DestinationSchema>`: Схеме назначения в DestinationCatalog.<br /><br /> `<DestinationTableName>`: Имя целевой таблицы или «TableName».<br /><br /> `<DestinationDatasource>`: Имя источника данных назначения.<br /><br /> `<Username>`и `<Password>`: эти поля указывают, что имя пользователя и пароль для назначения может потребоваться.<br /><br /> `<CreateStatement>`: Инструкции создания таблицы для целевой базы данных.|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: Идентификатор для результирующего набора.|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: Идентификатор созданного объекта.|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **ОБЪЯСНЯЕТСЯ** может применяться к *оптимизируемые* только запросы, которые являются запросы, которые может быть улучшена или изменено на основе результатов **ОБЪЯСНИТЬ** команды. Поддерживаемые **объяснение** перечисленных выше команд. Попытка использовать **объяснение** с запросом неподдерживаемый тип будут возвращать ошибку или эхо-запрос.  
  
 **ОБЪЯСНЯЕТСЯ** не поддерживается в пользовательской транзакции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан **объяснение** команду **ВЫБЕРИТЕ** инструкцию и результаты в формате XML.  
  
 **Отправка инструкции ОПИСАНИЯ**  
  
 В этом примере отправленной команда имеет вид:  
  
```  
USE AdventureWorksPDW2012;  
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
  
 После выполнения инструкции с помощью **объяснение** режим, вкладка «сообщение» содержит одну строку под названием **объяснить**и начинается с XML-текст `\<?xml version="1.0" encoding="utf-8"?>` щелкните XML, чтобы открыть весь текст в Окно «XML». Чтобы лучше понять следующими комментариями, необходимо включить отображение номеров строк в SSDT.  
  
#### <a name="to-turn-on-line-numbers"></a>Чтобы включить номера строк  
  
1.  С выводимая в **объяснить** вкладке SSDT на **средства** последовательно выберите пункты **параметры**.  
  
2.  Разверните **текстовый редактор** разверните **XML**, а затем нажмите кнопку **Общие**.  
  
3.  В **отображения** область проверки **номера строк**.  
  
4.  Нажмите кнопку **ОК**.  
  
 **Пример выходных данных ОПИСАНИЯ**  
  
 Результат XML **объяснение** команда с номерами строк включен:  
  
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
  
 **Значение ОПИСАНИЯ выходных данных**  
  
 Приведенном выше примере содержит 144 пронумерованных строк. Выходные данные из этого запроса может немного отличаться. В следующем списке описываются значительные разделов.  
  
-   Строки 3 – 16 введите описание запроса, который анализируется.  
  
-   Строка 17, указывает, что общее число операций будет 9. Начало каждой операции можно найти путем поиска по ключевым словам **dsql_operation**.  
  
-   Строки 18 запускает операцию 1. Указать, что строки 18 и 19 **RND_ID** операция создаст случайных Идентификационный номер, который будет использоваться для описания объекта. Объект, описанные в приведенном выше примере **TEMP_ID_16893**. Ваш номер будет отличаться.  
  
-   Строка 20 запускает операцию 2. Строки 21 до 25: на всех вычислительных узлов, создайте временную таблицу с именем **TEMP_ID_16893**.  
  
-   Строки 26 запускает операцию 3. 27 через 37 строк: переместить данные **TEMP_ID_16893** с помощью широковещательного перемещения. Предоставляется запроса, отправленного на каждом вычислительном узле. Указывает строки 37 целевая таблица **TEMP_ID_16893**.  
  
-   Строке 38 запускает операцию 4. Строки 39 до 40: создать случайный идентификатор таблицы. **TEMP_ID_16894** — номер идентификатора в предыдущем примере. Ваш номер будет отличаться.  
  
-   Строки 41 запускает операцию 5. Строки 42 через 46: на всех узлах создайте временную таблицу с именем **TEMP_ID_16894**.  
  
-   Строки 47 запускает операцию 6. Строки 48 до 91: перемещение данных из различных таблиц (включая **TEMP_ID_16893**) в таблицу **TEMP_ID_16894**, с помощью смещения операции перемещения. Предоставляется запроса, отправленного на каждом вычислительном узле. Строка 90 определяет целевую таблицу как **TEMP_ID_16894**. 91 строка указывает столбцы.  
  
-   Строки 92 запускает операцию 7. 93 строки через 97: на всех вычислительных узлов, удалить временную таблицу **TEMP_ID_16893**.  
  
-   Строки 98 запускает операцию 8. 99 строки через 135: возвращать результаты клиенту. Используется запрос для получения результатов.  
  
-   Строки 136 запускает операцию 9. Строки 137 по 140: на всех узлах удалить временную таблицу **TEMP_ID_16894**.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере показан **объяснение** команду **ВЫБЕРИТЕ** инструкцию и результаты в формате XML.  
  
 **Отправка инструкции ОПИСАНИЯ**  
  
 В этом примере отправленной команда имеет вид:  
  
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
  
 После выполнения инструкции с помощью **объяснение** режим, вкладка «сообщение» содержит одну строку под названием **объяснить**и начинается с XML-текст `\<?xml version="1.0" encoding="utf-8"?>` щелкните XML, чтобы открыть весь текст в Окно «XML». Чтобы лучше понять следующими комментариями, необходимо включить отображение номеров строк в SSDT.  
  
#### <a name="to-turn-on-line-numbers"></a>Чтобы включить номера строк  
  
1.  С выводимая в **объяснить** вкладке SSDT на **средства** последовательно выберите пункты **параметры**.  
  
2.  Разверните **текстовый редактор** разверните **XML**, а затем нажмите кнопку **Общие**.  
  
3.  В **отображения** область проверки **номера строк**.  
  
4.  Нажмите кнопку **ОК**.  
  
 **Пример выходных данных ОПИСАНИЯ**  
  
 Результат XML **объяснение** команда с номерами строк включен:  
  
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
  
 **Значение ОПИСАНИЯ выходных данных**  
  
 Приведенном выше примере содержит 144 пронумерованных строк. Выходные данные из этого запроса может немного отличаться. В следующем списке описываются значительные разделов.  
  
-   Строки 3 – 16 введите описание запроса, который анализируется.  
  
-   Строка 17, указывает, что общее число операций будет 9. Начало каждой операции можно найти путем поиска по ключевым словам **dsql_operation**.  
  
-   Строки 18 запускает операцию 1. Указать, что строки 18 и 19 **RND_ID** операция создаст случайных Идентификационный номер, который будет использоваться для описания объекта. Объект, описанные в приведенном выше примере **TEMP_ID_16893**. Ваш номер будет отличаться.  
  
-   Строка 20 запускает операцию 2. Строки 21 до 25: на всех вычислительных узлов, создайте временную таблицу с именем **TEMP_ID_16893**.  
  
-   Строки 26 запускает операцию 3. 27 через 37 строк: переместить данные **TEMP_ID_16893** с помощью широковещательного перемещения. Предоставляется запроса, отправленного на каждом вычислительном узле. Указывает строки 37 целевая таблица **TEMP_ID_16893**.  
  
-   Строке 38 запускает операцию 4. Строки 39 до 40: создать случайный идентификатор таблицы. **TEMP_ID_16894** — номер идентификатора в предыдущем примере. Ваш номер будет отличаться.  
  
-   Строки 41 запускает операцию 5. Строки 42 через 46: на всех узлах создайте временную таблицу с именем **TEMP_ID_16894**.  
  
-   Строки 47 запускает операцию 6. Строки 48 до 91: перемещение данных из различных таблиц (включая **TEMP_ID_16893**) в таблицу **TEMP_ID_16894**, с помощью смещения операции перемещения. Предоставляется запроса, отправленного на каждом вычислительном узле. Строка 90 определяет целевую таблицу как **TEMP_ID_16894**. 91 строка указывает столбцы.  
  
-   Строки 92 запускает операцию 7. 93 строки через 97: на всех вычислительных узлов, удалить временную таблицу **TEMP_ID_16893**.  
  
-   Строки 98 запускает операцию 8. 99 строки через 135: возвращать результаты клиенту. Используется запрос для получения результатов.  
  
-   Строки 136 запускает операцию 9. Строки 137 по 140: на всех узлах удалить временную таблицу **TEMP_ID_16894**.  
  
  


