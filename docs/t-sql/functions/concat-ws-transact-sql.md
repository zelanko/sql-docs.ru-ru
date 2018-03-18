---
title: "CONCAT_WS (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7d7932c1887c82b2a10702f9054706e4cf9bce71
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Сцепляет переменное число аргументов с помощью разделителя, указанного в первом аргументе. (Название функции `CONCAT_WS` означает *сцепить с разделителем*.)

##  <a name="syntax"></a>Синтаксис   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Аргументы   
separator  
Выражение любого символьного типа (`nvarchar`, `varchar`, `nchar` или `char`).

argument1, argument2, argument*N*  
Выражение любого типа.

## <a name="return-types"></a>Типы возвращаемых данных
Строка. Длина и тип зависят от входных данных.

## <a name="remarks"></a>Remarks   
`CONCAT_WS` принимает переменное количество аргументов и сцепляет их в одну строку, используя первый аргумент как разделитель. Для этого требуется разделитель и не менее двух аргументов. В противном случае возникает ошибка. Все аргументы неявно преобразуются в строковые типы и затем сцепляются. 

Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразовании типов данных см. в статье [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Обработка значений NULL

`CONCAT_WS` игнорирует параметр `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`.

Если все аргументы имеют значение NULL, то возвращается пустая строка типа `varchar(1)`. 

Значения NULL пропускаются во время объединения, и разделитель не добавляется. Это упрощает распространенную ситуацию объединения строк, среди которых часто встречаются пустые значения, например поле второго адреса. См. пример Б.

Если значения NULL должны включаться с разделителем, см. пример В использования функции `ISNULL`.

## <a name="examples"></a>Примеры   

### <a name="a--concatenating-values-with-separator"></a>A.  Объединение значений с разделителем
В приведенном ниже примере сцепляются три столбца из таблицы sys.databases, причем значения разделяются символами `- `.   

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
В приведенном ниже примере значения `NULL` в списке аргументов пропускаются.

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
В приведенном ниже примере используется запятая в качестве разделителя, и к результату в формате списка значений с разделителями-запятыми добавляется символ возврата каретки.

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

Функция CONCAT_WS пропускает значения NULL в столбцах. Если некоторые столбцы могут принимать значения NULL, обработайте их функцией `ISNULL` и предоставьте значение по умолчанию, как в следующем примере:

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

