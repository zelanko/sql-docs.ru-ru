---
title: "CONCAT_WS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 377db445118e55f1bdeec220f1e6701e9f89706c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Сцепляет переменное число аргументов с помощью разделителей, установленных в 1-й аргумент. (`CONCAT_WS` указывает *сцепить с разделителем*.)

##  <a name="syntax"></a>Синтаксис   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Аргументы   
разделитель  
Выражение любого типа (`nvarchar`, `varchar`, `nchar`, или `char`).

аргумент1, аргумент2, аргумент*N*  
— Это выражение любого типа.

## <a name="return-types"></a>Возвращаемые типы
Строка. Длина и тип зависят от входных данных.

## <a name="remarks"></a>Замечания   
`CONCAT_WS`принимает переменное число аргументов и объединяет их в одну строку, используя первый аргумент в качестве разделителя. Требуется разделитель, а также как минимум из двух аргументов; в противном случае возникает ошибка. Все аргументы неявно преобразуются в строковые типы, а затем объединяются. 

Неявное преобразование в строки выполняется по существующим правилам преобразования типов данных. Дополнительные сведения о преобразованиях типов данных см. в разделе [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Обработка значений NULL

`CONCAT_WS`игнорирует `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}` параметр.

Если все аргументы имеют значение null, возвращается пустая строка типа `varchar(1)` возвращается. 

Значения NULL учитываются во время объединения и не добавляет разделитель. Это облегчает распространенный сценарий объединение строк, которые часто имеют пустые значения, например второе поле адрес. См. пример б.

Если сценарий требует значения null для включения разделитель, см. пример C помощью `ISNULL` функции.

## <a name="examples"></a>Примеры   

### <a name="a--concatenating-values-with-separator"></a>A.  Объединение значений с разделителем
Следующий пример Сцепляет три столбца в таблице sys.databases, разделяя значения с `- `.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 — ПРОСТОЙ - НЕТ |
|2 - SIMPLE - НЕТ |
|3 — ПОЛНЫЙ - НЕТ |
|4 - SIMPLE - НЕТ |


### <a name="b--skipping-null-values"></a>Б.  Пропуск значений NULL
Следующий пример не учитывает `NULL` значения в списке аргументов.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>В.  Создание CSV-файла из таблицы
Следующий пример использует в качестве разделителя запятую и добавляет символ возврата каретки в результате формат отдельных значений столбца.

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

CONCAT_WS игнорирует значения NULL в столбцах. Если некоторые столбцы, допускающие значение NULL, заключите их в оболочку с `ISNULL` функцией и указать значение по умолчанию как в следующем примере:

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>См. также:
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)      


