---
title: sys.sp_cleanup_temporal_history | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 111986a771b9cfb156c0d37688565b39401411f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037227"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Удаляет все строки из темпоральной таблицы журнала, соответствующие заданного ПЕРИОДА HISTORY_RETENTION в одной транзакции.
  
## <a name="syntax"></a>Синтаксис  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Аргументы  

*@table_name*

Имя темпоральной таблицы, для какой хранения вызывается очистки.

*schema_name*

Имя схемы, принадлежит какой текущей темпоральной таблицы

*row_count_var* [выход]

Выходной параметр, возвращающий число удаленных строк. Если в таблице журнала имеет кластеризованный индекс columnstore, будет возвращать этот параметр всегда равно 0.
  
## <a name="remarks"></a>Примечания
Эта хранимая процедура может использоваться только с помощью темпоральных таблиц, что конечный период хранения по-настоящему.
Используйте эту хранимую процедуру только в том случае, если необходимо немедленно очистить все устаревшие строки из таблицы журнала. Вы должны знать, что он может иметь значительное влияние на журнал базы данных и подсистемы ввода-вывода, так как оно удаляет все подходящие строки в той же транзакции. 

Всегда рекомендуется полагаться на внутренний фоновой задачи очистки, что удаляет устаревшие строки с минимальным влиянием на регулярных рабочих нагрузок и базы данных в целом.

## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  

## <a name="example"></a>Пример

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>См. также

[Политики хранения темпоральных таблиц](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
