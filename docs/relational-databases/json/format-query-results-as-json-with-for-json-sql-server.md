---
description: Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)
title: Форматирование результатов запроса как JSON с помощью предложения FOR JSON
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f3621fcc105d7b03d2347bc723f2ddb552bc9e81
ms.sourcegitcommit: 346a37242f889d76cd783f55aeed98023c693610
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765707"
---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Вы можете отформатировать результаты запроса как JSON или экспортировать данные из SQL Server в формате JSON, добавив предложение **FOR JSON** к инструкции **SELECT**. Предложение **FOR JSON** упрощает клиентские приложения, делегируя форматирование выходных данных JSON из приложения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) является рекомендуемым редактором запросов JSON, так как он позволяет выполнять автоматическое форматирование результатов JSON (как показано в этой статье) вместо отображения плоской строки.
  
 При использовании предложения **FOR JSON** вы можете в явном виде указать структуру выходных данных JSON или дать определить ее структуре инструкции SELECT.  
  
-   Чтобы сохранить полный контроль над форматом выходных данных JSON, используйте **FOR JSON PATH**. Вы можете создавать объекты-оболочки и вкладывать сложные свойства друг в друга.  
  
-   Используйте **FOR JSON AUTO**, чтобы отформатировать выходные данные JSON автоматически на основе структуры инструкции SELECT.  
  
Ниже приведен пример инструкции **SELECT** с предложением **FOR JSON** и ее выходные данные.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png)
  
## <a name="option-1---you-control-output-with-for-json-path"></a>Вариант 1. Вы управляете выходными данными с помощью FOR JSON PATH
В режиме **PATH** можно использовать синтаксис с точкой — например, `'Item.UnitPrice'` — для форматирования вложенных выходных данных.  

Ниже приведен пример запроса, где режим **PATH** с предложением **FOR JSON** . В следующем примере также используется параметр **ROOT** для указания именованного корневого элемента. 
  
 ![Схема потока выходных данных FOR JSON](../../relational-databases/json/media/forjson-example1.png) 

### <a name="more-info-about-for-json-path"></a>Дополнительные сведения о FOR JSON PATH
Более подробные сведения и примеры см. в разделе [Форматирование вложенных выходных данных JSON с помощью режима PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="option-2---select-statement-controls-output-with-for-json-auto"></a>Вариант 2. Инструкция SELECT управляет выходными данными с помощью FOR JSON AUTO
В режиме **AUTO** структура инструкции SELECT определяет формат выходных данных JSON.

По умолчанию значения **NULL** не включаются в выходные данные. Это поведение можно изменить с помощью **INCLUDE_NULL_VALUES** .  

Ниже приведен пример запроса, где режим **AUTO** используется с предложением **FOR JSON** .

```sql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO;
```  

А вот возвращаемый JSON.

```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```

### <a name="2b---example-with-join-and-null"></a>2.b — пример с JOIN и NULL

В следующем примере `SELECT...FOR JSON AUTO` включает результаты JSON при соотношении связи "один ко многим" между данными из таблиц `JOIN`.

Отсутствие значения NULL в возвращаемом JSON также показано. Тем не менее можно переопределить это поведение по умолчанию с помощью ключевого слова `INCLUDE_NULL_VALUES` в предложении `FOR`.

```sql
go

DROP TABLE IF EXISTS #tabStudent;
DROP TABLE IF EXISTS #tabClass;

go

CREATE TABLE #tabClass
(
   ClassGuid   uniqueIdentifier  not null  default newid(),
   ClassName   nvarchar(32)      not null
);

CREATE TABLE #tabStudent
(
   StudentGuid   uniqueIdentifier  not null  default newid(),
   StudentName   nvarchar(32)      not null,
   ClassGuid     uniqueIdentifier      null   -- Foreign key.
);

go

INSERT INTO #tabClass
      (ClassGuid, ClassName)
   VALUES
      ('DE807673-ECFC-4850-930D-A86F921DE438', 'Algebra Math'),
      ('C55C6819-E744-4797-AC56-FF8A729A7F5C', 'Calculus Math'),
      ('98509D36-A2C8-4A65-A310-E744F5621C83', 'Art Painting')
;

INSERT INTO #tabStudent
      (StudentName, ClassGuid)
   VALUES
      ('Alice Apple', 'DE807673-ECFC-4850-930D-A86F921DE438'),
      ('Alice Apple', 'C55C6819-E744-4797-AC56-FF8A729A7F5C'),
      ('Betty Boot' , 'C55C6819-E744-4797-AC56-FF8A729A7F5C'),
      ('Betty Boot' , '98509D36-A2C8-4A65-A310-E744F5621C83'),
      ('Carla Cap'  , null)
;

go

SELECT
      c.ClassName,
      s.StudentName
   from
                       #tabClass   as c
      RIGHT OUTER JOIN #tabStudent as s ON s.ClassGuid = c.ClassGuid
   --where
   --   c.ClassName LIKE '%Math%'
   order by
      c.ClassName,
      s.StudentName
   FOR
      JSON AUTO
      --, INCLUDE_NULL_VALUES
;

go

DROP TABLE IF EXISTS #tabStudent;
DROP TABLE IF EXISTS #tabClass;

go
```

Вот JSON, который выводится предыдущей инструкцией SELECT.

```json
JSON_F52E2B61-18A1-11d1-B105-00805F49916B

[
   {"s":[{"StudentName":"Carla Cap"}]},
   {"ClassName":"Algebra Math","s":[{"StudentName":"Alice Apple"}]},
   {"ClassName":"Art Painting","s":[{"StudentName":"Betty Boot"}]},
   {"ClassName":"Calculus Math","s":[{"StudentName":"Alice Apple"},{"StudentName":"Betty Boot"}]}
]
```

### <a name="more-info-about-for-json-auto"></a>Дополнительные сведения о FOR JSON AUTO

Более подробные сведения и примеры см. в разделе [Автоматическое форматирование выходных данных JSON с помощью режима AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Сведения о синтаксисе и использовании см. в разделе [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Управление другими параметрами выходных данных JSON  
Управление выходными данными из **FOR JSON** предложения, используя следующие дополнительные параметры.  
  
-   **ROOT**. Чтобы добавить один элемент верхнего уровня в выходные данные JSON, укажите параметр **ROOT** . Если не указать этот параметр, выходные данные JSON не будут поддерживать корневой элемент. Дополнительные сведения см. в разделе [Добавление корневого узла в выходные данные JSON с параметром ROOT (SQL Server)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   **INCLUDE_NULL_VALUES**. Чтобы включить значения NULL в выходные данные JSON, укажите параметр **INCLUDE_NULL_VALUES** . Если не указать этот параметр, выходные данные не будут включать свойства JSON для значений NULL в результатах запроса. Дополнительные сведения см. в статье [Использование параметра INCLUDE_NULL_VALUES для включения значений Null в выходные данные JSON &#40;SQL Server&#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   **WITHOUT_ARRAY_WRAPPER**. Чтобы удалить квадратные скобки, в которые выходные данные JSON предложения **FOR JSON** заключаются по умолчанию, укажите параметр **WITHOUT_ARRAY_WRAPPER** . Используйте этот параметр, чтобы создать единый объект JSON в качестве выходных данных из одной строки результата. Если этот параметр не указан, выходные данные JSON форматируются как массив — то есть заключены в квадратные скобки. Дополнительные сведения см. в разделе [Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Выходные данные предложения FOR JSON  
Выходные данные предложения **FOR JSON** имеют следующие характеристики:  
  
1.  Результирующий набор содержит один столбец.
    -   Небольшой результирующий набор может содержать одну строку.
    -   Большой результирующий набор разбивает длинную строку JSON по нескольким строкам.
        -   По умолчанию SQL Server Management Studio (SSMS) сцепляет результаты в одну строку, если выходной параметр **В виде сетки**. В строке состояния SSMS отображается действительное число строк.
        -   В других клиентских приложениях может потребоваться внести код, который будет перераспределять большой объем результатов в одну общую допустимую строку JSON, объединяя содержимое множества записей. Пример этого кода в приложении C# см. в разделе [Использование выходных данных FOR JSON в клиентском приложении C#](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md#use-for-json-output-in-a-c-client-app).
  
     ![Пример выходных данных FOR JSON](../../relational-databases/json/media/forjson-example2.png)  
  
2.  Результаты форматируются в виде массива объектов JSON.  
  
    -   Число элементов в массиве JSON равно числу строк в результатах инструкции SELECT (до применения предложения FOR JSON). 
  
    -   Каждая строка в результатах инструкции SELECT (до применения предложения FOR JSON) становится отдельным объектом JSON в массиве.  
  
    -   Каждый столбец в результатах инструкции SELECT (до применения предложения FOR JSON) становится свойством объекта JSON.  
  
3.  Как имена столбцов, так и их значения экранируются согласно синтаксису JSON. Дополнительные сведения см. в разделе [Как FOR JSON экранирует специальные и управляющие символы (SQL Server)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).

### <a name="example"></a>Пример
Приведенный ниже пример показывает, каким образом предложение **FOR JSON** форматирует выходные данные JSON.  
  
**Результаты запроса**  

|Объект|B|C|D|
|-|-|-|-|
|10|11|12|X|  
|20|21|22|Да|  
|30|31|32|Z|  
| &nbsp; | &nbsp; | &nbsp; | &nbsp; |

 **Выходные данные JSON**  
  
```json  
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  

 Дополнительные сведения о том, какое содержимое отображается в выходных данных предложения **FOR JSON**, см. в следующих статьях.  

-   [Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
    Предложение **FOR JSON** использует правила, описанные в этом разделе, для преобразования типов данных SQL в типы JSON в выходных данных JSON.  

-   [Как FOR JSON экранирует специальные и управляющие символы (SQL Server)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
    Предложение **FOR JSON** экранирует специальные символы и представляет управляющие символы в выходных данных JSON, как описано в этом разделе.  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Использование выходных данных FOR JSON в SQL Server и клиентских приложениях &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  
