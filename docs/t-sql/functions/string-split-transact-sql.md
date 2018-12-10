---
title: STRING_SPLIT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5fb13510e4894e3f2bc77293a1f4aac0b186f1f0
ms.sourcegitcommit: f1cf91e679d1121d7f1ef66717b173c22430cb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "52586257"
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [Помогите улучшить документацию по SQL Server!](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Функция с табличным значением, которая разбивает строку на строки подстрок в зависимости от указанного знака разделения.

#### <a name="compatibility-level-130"></a>Уровень совместимости 130

STRING_SPLIT требует уровня совместимости не ниже 130. При уровне меньше 130 SQL Server не может найти функцию STRING_SPLIT.

Сведения об изменении уровня совместимости базы данных см. в статье [Просмотр или изменение уровня совместимости базы данных](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md).

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Аргументы  
 *строка*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (например, **nvarchar**, **varchar**, **nchar** или **char**).  
  
 *separator*  
 Отдельное [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (например, **nvarchar(1)**, **varchar(1)**, **nchar(1)** или **char(1)**), которое используется в качестве разделителя сцепленных подстрок.  
  
## <a name="return-types"></a>Типы возвращаемых данных  

Возвращает состоящую из одного столбца таблицу, строки которой являются подстроками. Имя столбца — **value**. Возвращает значение типа **nvarchar**, если любой из входных аргументов имеет тип **nvarchar** или **nchar**. В противном случае возвращает значение типа **varchar**. Длина типа возвращаемого значения равна длине аргумента string.  
  
## <a name="remarks"></a>Remarks  

**STRING_SPLIT** вводит строку с разделенными подстроками и один символ для использования в качестве разделителя. STRING_SPLIT выводит таблицу с одним столбцом, строки которого содержат подстроки. Имя выходного столбца — **value**.

Выходные строки могут быть расположены в любом порядке. Порядок _не_ обязательно совпадает с порядком подстрок во входной строке. Окончательный порядок сортировки можно переопределить с помощью предложения ORDER BY в инструкции SELECT (`ORDER BY value`).

Пустые строки нулевой длины присутствуют в том случае, если входная строка содержит два или несколько последовательных вхождений знака разделителя. Пустые подстроки обрабатываются так же, как и обычные подстроки. Можно отфильтровать строки, содержащие пустые подстроки, используя предложение WHERE (`WHERE value <> ''`). Если входная строка равна NULL, функция STRING_SPLIT с табличным значением возвращает пустую таблицу.  

Например, следующая инструкция SELECT использует символ пробела в качестве разделителя:

```sql
SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');
```

В пробном запуске предыдущая инструкция SELECT вернула следующую результирующую таблицу:  
  
|value|  
| :-- |  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
| &nbsp; |

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

Предыдущее использование STRING_SPLIT является заменой распространенного антишаблона. Такой антишаблон может включать создание динамической строки SQL на прикладном уровне или в Transact-SQL. Или антишаблон может осуществляться с помощью оператора LIKE. Смотрите следующий пример инструкции SELECT.

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
  
  
