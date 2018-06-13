---
title: STRING_SPLIT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5416e4c42e0aee104bc3fe23857a996b8b4b5981
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689162"
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Разделяет символьное выражение с использованием указанного разделителя.  
  
> [!NOTE]  
> Функция **STRING_SPLIT** доступна только при уровне совместимости 130 и выше. Если уровень совместимости базы данных меньше 130, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сможет найти и выполнить функцию **STRING_SPLIT**. Сведения об изменении уровня совместимости базы данных см. в статье [Просмотр или изменение уровня совместимости базы данных](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md).
> Имейте в виду, что уровень совместимости 120 может использоваться по умолчанию даже в новых [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Аргументы  
 *строка*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (например, **nvarchar**, **varchar**, **nchar** или **char**).  
  
 *separator*  
 Отдельное [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (например, **nvarchar(1)**, **varchar(1)**, **nchar(1)** или **char(1)**), которое используется в качестве разделителя сцепленных строк.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает состоящую из одного столбца таблицу с фрагментами. Имя столбца — **value**. Возвращает значение типа **nvarchar**, если любой из входных аргументов имеет тип **nvarchar** или **nchar**. В противном случае возвращает значение типа **varchar**. Длина типа возвращаемого значения равна длине аргумента string.  
  
## <a name="remarks"></a>Remarks  
Функция **STRING_SPLIT** принимает строку, которую следует разделить, и разделитель, с помощью которого строка будет разделена. Она возвращает состоящую из одного столбца таблицу с подстроками. Например, приведенная ниже инструкция `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');`, в которой в качестве разделителя используется символ пробела, возвращает следующую результирующую таблицу:  
  
|value|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
  
Если входная строка равна **NULL**, функция **STRING_SPLIT** с табличным значением возвращает пустую таблицу.  
  
Для функции **STRING_SPLIT** требуется режим совместимости не ниже 130.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-split-comma-separated-value-string"></a>A. Разделение строки значений с разделителями-запятыми  
Следующая инструкция анализирует разделенный запятыми список значений и возвращает все непустые токены:  
  
```sql  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
```  
  
Функция STRING_SPLIT вернет пустую строку, если между разделителями ничего нет. Condition RTRIM(value) <> '' удаляет пустые токены.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>Б. Разделение строки значений с разделителями-запятыми в столбце  
Таблица Product содержит столбец с разделенным запятыми списком тегов, как показано в следующем примере:  
  
|ProductId|Имя|Теги|  
|---------------|----------|----------|  
|1|Full-Finger Gloves|clothing,road,touring,bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike,mountain|  
  
Следующий запрос преобразовывает каждый список тегов и соединяет его с исходной строкой:  
  
```sql  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|Имя|value|  
|---------------|----------|-----------|  
|1|Full-Finger Gloves|clothing|  
|1|Full-Finger Gloves|road|  
|1|Full-Finger Gloves|touring|  
|1|Full-Finger Gloves|bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>В. Объединение по значениям  
Пользователю необходимо создать отчет, в котором приводится число продуктов по каждому тегу, причем теги упорядочены по числу продуктов, и отфильтрованы теги с более чем двумя продуктами.  
  
```sql  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>Г. Поиск по значению тега  
Разработчикам необходимо создать запросы для поиска статей по ключевым словам. Они могут использовать представленные ниже запросы.  
  
Поиск продуктов с одним тегом (clothing):  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
Поиск продуктов с двумя тегами (clothing и road):  
  
```sql  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>Д. Поиск строк по списку значений  
Разработчикам необходимо создать запрос, который находит статьи по списку идентификаторов. Они могут использовать следующий запрос:  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
Это альтернатива распространенному антишаблону, заключающемуся в создании динамической строки SQL на прикладном уровне или в [!INCLUDE[tsql](../../includes/tsql-md.md)] либо использовании оператора LIKE:  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>См. также:  
[LEFT (Transact-SQL)](../../t-sql/functions/left-transact-sql.md)     
[LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)     
[RIGHT (Transact-SQL)](../../t-sql/functions/right-transact-sql.md)    
[RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)     
[SUBSTRING (Transact-SQL)](../../t-sql/functions/substring-transact-sql.md)     
[TRIM (Transact-SQL)](../../t-sql/functions/trim-transact-sql.md)     
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)      
  
  
