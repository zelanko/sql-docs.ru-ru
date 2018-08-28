---
title: TRANSLATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ed5631256e47f38d2f329eafda4181190ab50c2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43068456"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Возвращает строку, предоставленную в качестве первого аргумента, после преобразования символов, указанных во втором аргументе, в конечный набор символов.

## <a name="syntax"></a>Синтаксис   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Аргументы   

inputString   
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа (nvarchar, varchar, nchar, char).

characters   
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа, содержащее символы, которые следует заменить.

переводы   
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) того же типа и длины, что и второй аргумент.

## <a name="return-types"></a>Типы возвращаемых данных   
Возвращает символьное выражение того же типа, что и `inputString`, в котором символы из второго аргумента заменены соответствующими символами из третьего аргумента.

## <a name="remarks"></a>Remarks   

Функция `TRANSLATE` возвращает ошибку, если символы и их замены имеют разную длину. Функция `TRANSLATE` должна возвращать входную строку без изменений, если в качестве символов или замен предоставлены значения NULL. Поведение функции `TRANSLATE` должно быть идентично поведению функции [REPLACE](../../t-sql/functions/replace-transact-sql.md).   

Поведение функции `TRANSLATE` эквивалентно использованию нескольких функций `REPLACE`.

`TRANSLATE` всегда учитывает параметры сортировки SC.

## <a name="examples"></a>Примеры   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Замена квадратных и фигурных скобок обычными    
Следующий запрос заменяет квадратные и фигурные скобки во входной строке на круглые:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  Функция `TRANSLATE` в этом примере эквивалентна следующей инструкции, в которой используется `REPLACE`, но гораздо проще ее: `SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>Б. Преобразование точек GeoJSON в WKT    
GeoJSON — это формат для кодирования различных структур географических данных. С помощью функции `TRANSLATE` разработчики могут легко преобразовывать точки GeoJSON в формат WKT, и наоборот. Следующий запрос заменяет квадратные и фигурные скобки во входной строке на обычные:   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Точка  |Координаты |  
---------|--------- |
(137.4 72.3) |[137.4,72.3] |


## <a name="see-also"></a>См. также:
 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

