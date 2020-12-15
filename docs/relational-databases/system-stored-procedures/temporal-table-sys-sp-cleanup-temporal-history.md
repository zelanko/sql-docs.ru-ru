---
description: sys.sp_cleanup_temporal_history (Transact-SQL)
title: sys.sp_cleanup_temporal_history | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-current
ms.openlocfilehash: e4afeb9f30040cf576a35b1b822bf5292752c148
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97427196"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys.sp_cleanup_temporal_history (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

Удаляет все строки из темпоральной таблицы журнала, которые соответствуют настроенному HISTORY_RETENTION ПЕРИОДу в рамках одной транзакции.

## <a name="syntax"></a>Синтаксис

```
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```

## <a name="arguments"></a>Аргументы

*\@table_name*

Имя темпоральной таблицы, для которой вызывается очистка хранения.

*schema_name*

Имя схемы, которой принадлежит текущая Темпоральная таблица

*row_count_var* [выходные данные]

Выходной параметр, возвращающий число удаленных строк. Если таблица журнала имеет кластеризованный индекс columnstore, этот параметр возвратит значение всегда 0.

## <a name="remarks"></a>Комментарии

Эта хранимая процедура может использоваться только с временными таблицами, для которых указан конечный срок хранения.
Используйте эту хранимую процедуру только в том случае, если необходимо немедленно очистить все устаревшие строки из таблицы журнала. Следует иметь в курсе, что он может оказать значительное влияние на журнал базы данных и подсистему ввода-вывода, так как он удаляет все подходящие строки в рамках одной транзакции.

Всегда рекомендуется полагаться на внутреннюю фоновую задачу для очистки, которая удаляет устаревшие строки с минимальным влиянием на обычные рабочие нагрузки и базу данных в целом.

## <a name="permissions"></a>Разрешения

Требуются db_owner разрешения.

## <a name="example"></a>Пример

```sql
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="next-steps"></a>Дальнейшие действия

[Политика хранения временных таблиц](/azure/sql-database/sql-database-temporal-tables-retention-policy)