---
title: "ПЕРЕВОД (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e7ea679043b83d8cee26f431602450d023516647
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="translate-transact-sql"></a>ПЕРЕВОД (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает строку, предоставленных в качестве первого аргумента, после некоторых символов, указанных во втором аргументе преобразуются в целевой набор символов.

## <a name="syntax"></a>Синтаксис   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Аргументы   

inputString   
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (nvarchar, varchar, nchar, char).

Символы   
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа, содержащих символы, которые должны быть заменены.

переводы   
Символом [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , соответствующий второй аргумент, тип и длину.

## <a name="return-types"></a>Типы возвращаемых значений   
Возвращает символьное выражение того же типа, что `inputString` где символов из второй аргумент заменяются сопоставления символов из третьего аргумента.

## <a name="remarks"></a>Remarks   

`TRANSLATE`функция возвращает ошибку, если имеют разные длины, символы и переводы. `TRANSLATE`функция должна возвращать входных данных без изменений, если значения null, представлены в виде символов или замены аргументов. Поведение `TRANSLATE` функции должен быть идентичен [заменить](../../t-sql/functions/replace-transact-sql.md) функции.   

Поведение `TRANSLATE` функция эквивалентна использования нескольких `REPLACE` функции.

`TRANSLATE`учитывает всегда параметрами сортировки SC.

## <a name="examples"></a>Примеры   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Замените квадратные и фигурные скобки регулярного фигурные скобки    
Следующий запрос заменяет квадратные и фигурные скобки во входной строке круглые скобки:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  `TRANSLATE` Функция в этом примере эквивалентно, но значительно упрощенной чем следующие инструкции, использующей `REPLACE`:`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>Б. Преобразовать GeoJSON точки в формате WKT    
GeoJSON — это формат для кодирования с различными структурами географические данные. С `TRANSLATE` функции, разработчики можно легко преобразовать GeoJSON точки в формате WKT и наоборот. Следующий запрос заменяет квадратные и фигурные скобки во входном файле регулярного фигурные скобки:   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Точка  |Координаты |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>См. также
 [CONCAT &#40; Transact-SQL &#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40; Transact-SQL &#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [Заменить &#40; Transact-SQL &#41;](../../t-sql/functions/replace-transact-sql.md)  
 [ОБРАТИТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40; Transact-SQL &#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40; Transact-SQL &#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

