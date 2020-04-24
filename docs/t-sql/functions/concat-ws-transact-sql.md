---
title: CONCAT_WS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: af7ce381b1a0fdef6db197e8e764d137cf641b7c
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635405"
---
# <a name="concat_ws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-asdw-xxx-md.md)]

Эта функция возвращает строку, возникающую в результате объединения двух или более строковых значений в сквозной форме. Она разделяет значения в такой объединенной строке с помощью разделителя, указанного в первом аргументе функции. (Название функции `CONCAT_WS` означает *сцепить с разделителем*.)

##  <a name="syntax"></a>Синтаксис   
```syntaxsql
CONCAT_WS ( separator, argument1, argument2 [, argumentN]... )
```

## <a name="arguments"></a>Аргументы   
separator  
Выражение любого символьного типа (`char`, `nchar`, `nvarchar` или `varchar`).

argument1, argument2, argument*N*  
Выражение любого типа.

## <a name="return-types"></a>Типы возвращаемых данных
Строковое значение, длина и тип которого зависят от входных данных.

## <a name="remarks"></a>Remarks   
`CONCAT_WS` принимает переменное количество строковых аргументов и объединяет их в одну строку. Она разделяет значения в такой объединенной строке с помощью разделителя, указанного в первом аргументе функции. Для `CONCAT_WS` требуется аргумент разделителя и как минимум два других аргумента строкового значения. Иначе `CONCAT_WS` вызовет ошибку. Функция `CONCAT_WS` неявно преобразует все аргументы в строковые типы перед объединением. 

Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразовании типов данных см. в статье [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Обработка значений NULL

`CONCAT_WS` игнорирует параметр `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`.

Если функция `CONCAT_WS` получает аргументы со всеми значениями NULL, она возвращает пустую строку типа varchar(1).

`CONCAT_WS` пропускает значения NULL во время объединения, и разделитель между ними не добавляется. Таким образом `CONCAT_WS` позволяет точно объединить строки, которые могут иметь пустые значения, например второе поле адреса. Дополнительные сведения см. в примере Б.

Если сценарий включает значения NULL, указанные через разделитель, рекомендуем использовать функцию `ISNULL`. Дополнительные сведения см. в примере В.

## <a name="examples"></a>Примеры   

### <a name="a--concatenating-values-with-separator"></a>A.  Объединение значений с разделителем
В этом примере объединяются три столбца из таблицы sys.databases, причем значения разделяются символами `-`.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NONE |
|2 - SIMPLE - NONE |
|3 - FULL - NONE |
|4 - SIMPLE - NONE |


### <a name="b--skipping-null-values"></a>Б.  Пропуск значений NULL
В этом примере значения `NULL` в списке аргументов пропускаются.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>В.  Создание CSV-файла на основе таблицы
В этом примере в качестве разделителя используется запятая `,`, и к результирующему набору в формате столбца значений с разделителями-запятыми добавляется символ возврата каретки `char(13)`.

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, recovery_model_desc, containment_desc), char(13)) AS DatabaseInfo
FROM sys.databases
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
DatabaseInfo
------------   
1,SIMPLE,NONE
2,SIMPLE,NONE
3,FULL,NONE 
4,SIMPLE,NONE 
```

CONCAT_WS пропускает значения NULL в столбцах. Перенесите столбец, допускающий значения NULL, с помощью функции `ISNULL` и укажите значение по умолчанию. Чтобы получить дополнительные сведения, см. следующий пример:

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>См. также раздел
 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE (Transact-SQL)](../../t-sql/functions/translate-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  

