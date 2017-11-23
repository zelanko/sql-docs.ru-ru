---
title: "sys.sp_cleanup_temporal_history | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-database
ms.service: sql-database
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
caps.latest.revision: "4"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed631f41e1ce49bfa431645b5f439925190198c7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="temporal-table---sysspcleanuptemporalhistory"></a>Временная таблица - sys.sp_cleanup_temporal_history
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Удаляет все строки из таблицы журнала, которые соответствуют настроенным HISTORY_RETENTION ПЕРИОДУ в одной транзакции.
  
## <a name="syntax"></a>Синтаксис  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Аргументы  

*@table_name*

Имя временной таблицы для хранения, который вызывается очистки.

*schema_name*

Имя схемы, принадлежит какой текущей темпоральной таблицы

*row_count_var* [выход]

Выходной параметр, возвращающий число удаленных строк. Если таблица журнала имеет кластеризованный индекс columnstore, будет возвращать этот параметр всегда имеет значение 0.
  
## <a name="remarks"></a>Замечания
Эта хранимая процедура может использоваться только с помощью темпоральных таблиц, имеют ограниченное указан срок хранения.
Используйте эту хранимую процедуру только в том случае, если необходимо немедленно очистить все устаревшие строки из таблицы журнала. Вы должны знать, что он может иметь значительное влияние на базу данных журнала и подсистемы ввода-вывода, как оно удаляет все подходящие строки в той же транзакции. 

Рекомендуется всегда полагаться на внутренние фоновой задачи очистки, удаляет устаревшие строки с минимальным влиянием на регулярных рабочих нагрузок и баз данных в целом.

## <a name="permissions"></a>Permissions  
 Требуются права db_owner.  

## <a name="example"></a>Пример

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>См. также:

[Политика хранения временных таблиц](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
