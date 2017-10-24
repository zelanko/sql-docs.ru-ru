---
title: "JSON_QUERY (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON_QUERY
- JSON_QUERY_TSQL
helpviewer_keywords:
- JSON, extracting
- JSON, querying
- JSON_QUERY function
ms.assetid: 1ab0d90f-19b6-4988-ab4f-22fdf28b7c79
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 56b50c0497a2e0ee40f9cf086124eba8e55bdd03
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="jsonquery-transact-sql"></a>JSON_QUERY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Извлекает объект или массив из строки JSON.  
  
 Чтобы извлечь скалярное значение из строки JSON, а не объект или массив, в разделе [JSON_VALUE &#40; Transact-SQL &#41; ](../../t-sql/functions/json-value-transact-sql.md). Сведения о различиях между **JSON_VALUE** и **JSON_QUERY**, в разделе [сравнение JSON_VALUE и JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
JSON_QUERY ( expression [ , path ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение. Обычно имя переменной или столбца, содержащего текст JSON.  
  
 Если **JSON_QUERY** находит JSON, который не является допустимым в *выражение* поиск значение определяется *путь*, функция возвращает ошибку. Если **JSON_QUERY** не находит значение определяется *путь*, он просматривает весь текст, и возвращает ошибку, если он найдет JSON является недопустимым в любом месте *выражение*.  
  
 *путь*  
 Путь JSON, указывающее объект или массив для извлечения.

В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], можно ввести в качестве значения переменной *путь*.

Путь JSON можно указать режим значениями lax или strict для синтаксического анализа. Если не указать режим анализа, нестрогой режим используется по умолчанию. Дополнительные сведения см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  

Значение по умолчанию для *путь* «$». В результате, если не указать значение для *путь*, **JSON_QUERY** Возвращает входные данные *выражение*.

Если формат *путь* является недопустимой, **JSON_QUERY** возвращает сообщение об ошибке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает фрагмент JSON типа nvarchar(max). Параметры сортировки для возвращаемого значения является совпадают с параметрами сортировки входного выражения.  
  
 Если значение не объект или массив:  
  
-   В режиме нестрогой **JSON_QUERY** возвращает значение null.  
  
-   В строгом режиме **JSON_QUERY** возвращает сообщение об ошибке.  
  
## <a name="remarks"></a>Замечания  

### <a name="lax-mode-and-strict-mode"></a>Нестрогая и строгий режим

 Рассмотрим следующий текст JSON.  
  
```json  
{
    "info": {
        "type": 1,
        "address": {
            "town": "Bristol",
            "county": "Avon",
            "country": "England"
        },
        "tags": ["Sport", "Water polo"]
    },
    "type": "Basic"
} 
```  
  
 В следующей таблице сравниваются поведение **JSON_QUERY** в нестрогой режиме и в строгом режиме. Дополнительные сведения о спецификации режим дополнительный путь (значениями lax или strict) см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Путь|Возвращаемое значение в режиме нестрогой|Возвращаемое значение в строгом режиме|Дополнительные сведения|  
|----------|------------------------------|---------------------------------|---------------|  
|$|Возвращает весь текст JSON.|Возвращает весь текст JSON.|Недоступно|  
|$. info.type|NULL|Ошибка|Не объект или массив.<br /><br /> Используйте **JSON_VALUE** вместо него.|  
|$. info.address.town|NULL|Ошибка|Не объект или массив.<br /><br /> Используйте **JSON_VALUE** вместо него.|  
|$.info.» адрес»|N'{«Город»: «Бристольский», «район»: «Avon», «Страна»: «Англия»} "|N'{«Город»: «Бристольский», «район»: «Avon», «Страна»: «Англия»} "|Недоступно|  
|$. info.tags|N «[«Спорт», «Вода polo»]»|N «[«Спорт», «Вода polo»]»|Недоступно|  
|$. info.type[0]|NULL|Ошибка|Не массив.|  
|$. info.none|NULL|Ошибка|Свойство не существует.|  

### <a name="using-jsonquery-with-for-json"></a>JSON_QUERY при помощи предложения FOR JSON

**JSON_QUERY** возвращает допустимый фрагмент JSON. В результате **FOR JSON** не экранирует специальные символы в **JSON_QUERY** возвращаемое значение.

Если возврат результатов с помощью предложения FOR JSON, а при включении данные, которые уже находится в формате JSON (в столбце или в результате выражение), перенос данных JSON с помощью **JSON_QUERY** без *путь* параметр.

## <a name="examples"></a>Примеры  
  
### <a name="example-1"></a>Пример 1  
 В следующем примере показано, как можно вернуть фрагмент JSON из `CustomFields` столбца в результатах запроса.  
  
```sql  
SELECT PersonID,FullName,
 JSON_QUERY(CustomFields,'$.OtherLanguages') AS Languages
FROM Application.People
```  
  
### <a name="example-2"></a>Пример 2  
Приведенный ниже показано, как включить фрагменты JSON в выходных данных предложения FOR JSON.  
  
```sql  
SELECT StockItemID, StockItemName,
         JSON_QUERY(Tags) as Tags,
         JSON_QUERY(CONCAT('["',ValidFrom,'","',ValidTo,'"]')) ValidityPeriod
FROM Warehouse.StockItems
FOR JSON PATH
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Данные JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  

