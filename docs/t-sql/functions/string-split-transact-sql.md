---
title: "STRING_SPLIT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 049bdf1021d57e28ed94e11c89aa997ee0eba5e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Разделяет символьное выражение, используя заданный разделитель.  
  
> [!NOTE]  
>  **STRING_SPLIT** функция доступна только при уровне совместимости 130. Если уровень совместимости базы данных ниже 130, SQL Server не будет иметь возможность поиска и выполнения **STRING_SPLIT** функции. Изменить уровень совместимости базы данных можно с помощью следующей команды:  
> ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
>   
>  Обратите внимание, что уровень совместимости 120 может по умолчанию даже в новых базах данных SQL Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Аргументы  
 *строка*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (т. е. **nvarchar**, **varchar**, **nchar** или **char**).  
  
 *разделитель*  
 — Это отдельный символ [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (например **nvarchar(1)**, **varchar(1)**, **nchar(1)** или  **char(1)**), используемый в качестве разделителя для сцепленные строки.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает один столбец таблицы с помощью фрагментов. Имя столбца — **значение**. Возвращает **nvarchar** Если какой-либо из входных аргументов **nvarchar** или **nchar**. В противном случае возвращает **varchar**. Длина возвращаемого типа является таким же, как длина строковый аргумент.  
  
## <a name="remarks"></a>Замечания  
 **STRING_SPLIT** принимает строку, которая должна быть разделена и разделитель, который будет использоваться для разделения строки. Он возвращает один столбец таблицы с подстроками. Например, следующая инструкция `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` с помощью символа пробела в качестве разделителя, возвращаются следующие таблицы результатов:  
  
|value|  
|-----------|  
|Lorem|  
|Ipsum|  
|dolor|  
|SIT|  
|Amet.|  
  
 Если входная строка **NULL**, **STRING_SPLIT** табличная функция возвращает пустую таблицу.  
  
 **STRING_SPLIT** требуется по крайней мере режим совместимости 130.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-split-comma-separated-value-string"></a>A. Разделить запятыми строковое значение  
 Синтаксический анализ разделенный запятыми список значений и возвращают все маркеры пустым:  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 STRING_SPLIT возвращает пустую строку, если нет ничего между разделителем. Условие RTRIM(value) <> '' приведет к удалению пустой маркеры.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>Б. Разделить запятыми строковое значение в столбце  
 Таблица Product содержит столбец с разделителями отдельные список тегов, показано в следующем примере:  
  
|productId|Имя|Теги|  
|---------------|----------|----------|  
|1|Full пальцем перчатки|одежда, дорожный, туристического велосипеда|  
|2|Головные LL|велосипеда|  
|3|HL Mountain Frame|велосипед, mountain|  
  
 Следующий запрос преобразует каждый список тегов и объединяет их с исходной строки:  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|productId|Имя|value|  
|---------------|----------|-----------|  
|1|Full пальцем перчатки|одежда|  
|1|Full пальцем перчатки|дорога|  
|1|Full пальцем перчатки|Туристический|  
|1|Full пальцем перчатки|велосипеда|  
|2|Головные LL|велосипеда|  
|3|HL Mountain Frame|велосипеда|  
|3|HL Mountain Frame|Mountain|  
  
### <a name="c-aggregation-by-values"></a>В. Агрегат по значениям  
 Пользователям необходимо создать отчет, показывающий количество продуктов на каждого тега, отсортированный по номеру продуктов и фильтрации только теги с более чем двумя продуктами.  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>Г. Поиск по значению тега  
 Разработчики должны создавать запросов на поиск статей по ключевым словам. Они могут использовать следующие запросы:  
  
 Для поиска продуктов с помощью одного тега (одежды):  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 Найти продукты с два указанного тега (одежды и пути):  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>Д. Поиск строк по списку значений  
 Разработчикам необходимо создать запрос на поиск статей по список идентификаторов. Их можно использовать следующий запрос:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 Это замена для общих антишаблон, например для создания динамической строке SQL на уровне приложения или [!INCLUDE[tsql](../../includes/tsql-md.md)], или используя оператор LIKE:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>См. также:  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
  
  

