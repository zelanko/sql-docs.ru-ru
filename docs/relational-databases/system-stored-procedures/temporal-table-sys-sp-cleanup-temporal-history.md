---
title: sys. sp_cleanup_temporal_history | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6f382af39620fde58480b9fa02178901cb882dab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251999"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys. sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Удаляет все строки из темпоральной таблицы журнала, которые соответствуют настроенной HISTORY_RETENTION ПЕРИОДу в рамках одной транзакции.
  
## <a name="syntax"></a>Синтаксис  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Аргументы  

*@no__t 1table_name*

Имя темпоральной таблицы, для которой вызывается очистка хранения.

*schema_name*

Имя схемы, которой принадлежит текущая Темпоральная таблица

*row_count_var* [выходные данные]

Выходной параметр, возвращающий число удаленных строк. Если таблица журнала имеет кластеризованный индекс columnstore, этот параметр возвратит значение всегда 0.
  
## <a name="remarks"></a>Примечания
Эта хранимая процедура может использоваться только с временными таблицами, для которых указан конечный срок хранения.
Используйте эту хранимую процедуру только в том случае, если необходимо немедленно очистить все устаревшие строки из таблицы журнала. Следует иметь в курсе, что он может оказать значительное влияние на журнал базы данных и подсистему ввода-вывода, так как он удаляет все подходящие строки в рамках одной транзакции. 

Всегда рекомендуется полагаться на внутреннюю фоновую задачу для очистки, которая удаляет устаревшие строки с минимальным влиянием на обычные рабочие нагрузки и базу данных в целом.

## <a name="permissions"></a>Разрешения  
 Требуются разрешения db_owner.  

## <a name="example"></a>Пример

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>См. также

[Политика хранения временных таблиц](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
