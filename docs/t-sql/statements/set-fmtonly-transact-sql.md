---
title: SET FMTONLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FMTONLY_TSQL
- FMTONLY
- SET FMTONLY
- SET_FMTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], only metadata returned
- SET FMTONLY statement
- FMTONLY option
ms.assetid: 02a1d9ac-2e58-433c-9a07-2c5a4a2214e1
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d150082120cde1b09d3437a27b2345b036daf8b5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67929027"
---
# <a name="set-fmtonly-transact-sql"></a>SET FMTONLY (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss-all-md](../../includes/tsql-appliesto-ss-all-md.md)]

  Возвращает клиенту только метаданные. Может использоваться для тестирования формата ответа без фактического выполнения запроса.  

> [!NOTE]
> Не используйте эту функцию. Эта функция заменена следующими:
>
> - [sp_describe_first_result_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)
> - [sp_describe_undeclared_parameters (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)
> - [sys.dm_exec_describe_first_result_set (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)
> - [sys.dm_exec_describe_first_result_set_for_object (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET FMTONLY { ON | OFF }   
```  

## <a name="remarks"></a>Remarks

Когда `FMTONLY` является `ON`, возвращается набор строк с именами столбцов, но не строки данных.

`SET FMTONLY ON` не оказывает влияния при анализе пакета Transact-SQL. Эффект возникает во время выполнения.

Значение по умолчанию — `OFF`.

## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  

## <a name="examples"></a>Примеры

В следующем примере кода Transact-SQL `FMTONLY` задается как `ON`. Этот параметр заставляет SQL Server возвращать только метаданные о выбранных столбцах. А именно, возвращаются имена столбцов. Строки данных не возвращаются.

В примере тестовое выполнение хранимой процедуры `prc_gm29` возвращает следующее:

- Несколько наборов строк.
- Столбцы из нескольких таблиц в одной из его инструкций `SELECT`.

<!--
Issue 2246 inspired this code example, and the replacement of the two pre-existing examples. 2019/June/03, GM.
-->

```sql
go
SET NoCount ON;

go
DROP PROCEDURE IF EXISTS prc_gm29;

DROP Table IF EXISTS #tabTemp41;
DROP Table IF EXISTS #tabTemp42;
go

CREATE TABLE #tabTemp41
(
   KeyInt41        int           not null,
   Name41          nvarchar(16)  not null,
   TargetDateTime  datetime      not null  default GetDate()
);

CREATE TABLE #tabTemp42
(
   KeyInt42 int          not null,   -- JOIN-able to KeyInt41.
   Name42   nvarchar(16) not null
);
go

INSERT into #tabTemp41 (KeyInt41, Name41) values (10, 't41-c');
INSERT into #tabTemp42 (KeyInt42, Name42) values (10, 't42-p');
go

CREATE PROCEDURE prc_gm29
AS
begin
SELECT * from #tabTemp41;
SELECT * from #tabTemp42;

SELECT t41.KeyInt41, t41.TargetDateTime, t41.Name41, t42.Name42
   from
                 #tabTemp41 as t41
      INNER JOIN #tabTemp42 as t42 on t42.KeyInt42 = t41.KeyInt41
end;
go

SET DATEFORMAT mdy;

SET FMTONLY ON;
EXECUTE prc_gm29;   -- Returns multiple tables.
SET FMTONLY OFF;
go
DROP PROCEDURE IF EXISTS prc_gm29;

DROP Table IF EXISTS #tabTemp41;
DROP Table IF EXISTS #tabTemp42;
go

/****  Actual Output:
[C:\JunkM\]
>> osql.exe -S myazuresqldb.database.windows.net -U somebody -P secret -d MyDatabase -i C:\JunkM\Issue-2246-a.SQL 

 KeyInt41    Name41           TargetDateTime
 ----------- ---------------- -----------------------

 KeyInt42    Name42
 ----------- ----------------

 KeyInt41    TargetDateTime          Name41           Name42
 ----------- ----------------------- ---------------- ----------------


[C:\JunkM\]
>>
****/
```

## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

