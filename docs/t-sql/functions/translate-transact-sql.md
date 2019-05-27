---
title: TRANSLATE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/01/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2f278b257b1e14f88743a03098949712fa7a873
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65946667"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Возвращает строку, предоставленную в качестве первого аргумента, после преобразования символов, указанных во втором аргументе, в конечный набор символов, указанный в третьем аргументе.

## <a name="syntax"></a>Синтаксис

```sql
TRANSLATE ( inputString, characters, translations)
```

## <a name="arguments"></a>Аргументы

 *inputString* — это строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md), в котором выполняется поиск. *inputString* может быть любого символьного типа данных (nvarchar, varchar, nchar, char).

 *characters* — это строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md), содержащее символы, которые следует заменить. *characters* может быть любого символьного типа данных.

*translations* — это строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md), содержащее заменяющие символы. *translations* должен иметь один и тот же тип данных и длину, что и *characters*.

## <a name="return-types"></a>Типы возвращаемых данных

Возвращает символьное выражение того же типа даты, что и `inputString`, в котором символы из второго аргумента заменены соответствующими символами из третьего аргумента.

## <a name="remarks"></a>Remarks

`TRANSLATE` возвращает ошибку, если выражения *characters* и *translations* имеют разную длину. `TRANSLATE` возвращает значение NULL, если любой из аргументов имеет значение NULL.  

Поведение функции `TRANSLATE` аналогично использованию нескольких функций [REPLACE](../../t-sql/functions/replace-transact-sql.md). `TRANSLATE`, однако, не заменяет символы более одного раза. Это отличает ее от нескольких функций `REPLACE`, так как каждая из них пытается заменить все соответствующие символы. 

`TRANSLATE` всегда учитывает параметры сортировки SC.

## <a name="examples"></a>Примеры

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Замена квадратных и фигурных скобок обычными

Следующий запрос заменяет квадратные и фигурные скобки во входной строке на круглые:

```sql
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

```plain_text
2*(3+4)/(7-2)
```

#### <a name="equivalent-calls-to-replace"></a>Эквивалентные вызовы функции REPLACE

В следующей инструкции SELECT имеется группа из четырех вложенных вызовов функции REPLACE. Эта группа эквивалентна одному вызову функции TRANSLATE в предыдущей инструкции SELECT:

```sql
SELECT
REPLACE
(
      REPLACE
      (
            REPLACE
            (
                  REPLACE
                  (
                        '2*[3+4]/{7-2}',
                        '[',
                        '('
                  ),
                  ']',
                  ')'
            ),
            '{',
            '('
      ),
      '}',
      ')'
);
```

### <a name="b-convert-geojson-points-into-wkt"></a>Б. Преобразование точек GeoJSON в WKT

GeoJSON — это формат для кодирования различных структур географических данных. С помощью функции `TRANSLATE` разработчики могут легко преобразовывать точки GeoJSON в формат WKT, и наоборот. Следующий запрос заменяет квадратные и фигурные скобки во входной строке на обычные:

```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Точка  |Координаты |  
|---------|--------- |
|(137.4 72.3) |[137.4,72.3] |

### <a name="c-use-the-translate-function"></a>В. Используйте функцию TRANSLATE

```sql
SELECT TRANSLATE('abcdef','abc','bcd') AS Translated,
       REPLACE(REPLACE(REPLACE('abcdef','a','b'),'b','c'),'c','d') AS Replaced;
```

Результаты:

| Переведенный текст | Замененный текст |  
| ---------|--------- |
| bcddef | ddddef |


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
