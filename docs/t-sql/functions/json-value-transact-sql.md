---
title: "JSON_VALUE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON_VALUE
- JSON_VALUE_TSQL
helpviewer_keywords:
- JSON_VALUE function
- JSON, extracting
- JSON, querying
ms.assetid: cd016e14-11eb-4eaf-bf05-c7cfcc820a10
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab4c14769dc51c6d5b97a6ad2fe6f0cb06fad4e0
ms.sourcegitcommit: 19e1c4067142d33e8485cb903a7a9beb7d894015
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2017
---
# <a name="jsonvalue-transact-sql"></a>JSON_VALUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Извлекает скалярное значение из строки JSON.  
  
 Чтобы извлечь объект или массив из строки JSON вместо скалярного значения, в разделе [JSON_QUERY &#40; Transact-SQL &#41; ](../../t-sql/functions/json-query-transact-sql.md). Сведения о различиях между **JSON_VALUE** и **JSON_QUERY**, в разделе [сравнение JSON_VALUE и JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
JSON_VALUE ( expression , path )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение. Обычно имя переменной или столбца, содержащего текст JSON.  
 
 Если **JSON_VALUE** находит JSON, который не является допустимым в *выражение* поиск значение определяется *путь*, функция возвращает ошибку. Если **JSON_VALUE* не находит значение определяется *путь*, он просматривает весь текст, и возвращает ошибку, если он найдет JSON является недопустимым в любом месте *выражение*.
  
 *путь*  
 Путь JSON, который определяет свойство для извлечения. Дополнительные сведения см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
 
В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], можно ввести в качестве значения переменной *путь*.
  
 Если формат *путь* является недопустимой, **JSON_VALUE** возвращает сообщение об ошибке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает тип nvarchar(4000) одно текстовое значение. Параметры сортировки для возвращаемого значения является совпадают с параметрами сортировки входного выражения.  
  
 Если значение превышает 4000 символов:  
  
-   В режиме нестрогой **JSON_VALUE** возвращает значение null.  
  
-   В строгом режиме **JSON_VALUE** возвращает сообщение об ошибке.  
  
 Если для возврата скалярных значений больше, чем 4 000 символов, используйте **OPENJSON** вместо **JSON_VALUE**. Дополнительные сведения см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="remarks"></a>Замечания

### <a name="lax-mode-and-strict-mode"></a>Нестрогая и строгий режим

 Рассмотрим следующий текст JSON.  
  
```json  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'  
```  
  
 В следующей таблице сравниваются поведение **JSON_VALUE** в нестрогой режиме и в строгом режиме. Дополнительные сведения о спецификации режим дополнительный путь (значениями lax или strict) см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Путь|Возвращаемое значение в режиме нестрогой|Возвращаемое значение в строгом режиме|Дополнительные сведения|  
|----------|------------------------------|---------------------------------|---------------|  
|$|NULL|Ошибка|Скалярное значение.<br /><br /> Используйте **JSON_QUERY** вместо него.|  
|$. info.type|N '1'|N '1'|Недоступно|  
|$. info.address.town|N'Bristol "|N'Bristol "|Недоступно|  
|$.info.» адрес»|NULL|Ошибка|Скалярное значение.<br /><br /> Используйте **JSON_QUERY** вместо него.|  
|$. info.tags|NULL|Ошибка|Скалярное значение.<br /><br /> Используйте **JSON_QUERY** вместо него.|  
|$. info.type[0]|NULL|Ошибка|Не массив.|  
|$. info.none|NULL|Ошибка|Свойство не существует.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="example-1"></a>Пример 1  
 В следующем примере значения свойств JSON `town` и `state` в результатах запроса. Поскольку **JSON_VALUE** сохраняет параметры сортировки источника, порядок сортировки результатов зависит от параметров сортировки `jsonInfo` столбца. 

> [!NOTE]
> (В этом примере предполагается, что имя таблицы `Person.Person` содержит `jsonInfo` столбец текста JSON, а этот столбец имеет структуру, показанному ранее в обсуждение нестрогой и строгий режим. В образце базы данных AdventureWorks `Person` таблица на самом деле не содержать `jsonInfo` столбца.)
  
```sql  
SELECT FirstName, LastName,
 JSON_VALUE(jsonInfo,'$.info.address[0].town') AS Town
FROM Person.Person
WHERE JSON_VALUE(jsonInfo,'$.info.address[0].state') LIKE 'US%'
ORDER BY JSON_VALUE(jsonInfo,'$.info.address[0].town')
```  
  
### <a name="example-2"></a>Пример 2  
 Следующий пример извлекает значение свойства JSON `town` в локальную переменную.  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)
DECLARE @town NVARCHAR(32)

SET @jsonInfo=N'<array of address info>'

SET @town=JSON_VALUE(@jsonInfo,'$.info.address.town')
```  
  
### <a name="example-3"></a>Пример 3  
 В следующем примере создается на основе значений свойств JSON вычисляемых столбцов.  
  
```sql  
CREATE TABLE dbo.Store
 (
  StoreID INT IDENTITY(1,1) NOT NULL,
  Address VARCHAR(500),
  jsonContent NVARCHAR(8000),
  Longitude AS JSON_VALUE(jsonContent, '$.address[0].longitude'),
  Latitude AS JSON_VALUE(jsonContent, '$.address[0].latitude')
 )
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Данные JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
