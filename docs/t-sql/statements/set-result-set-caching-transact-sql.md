---
title: SET RESULT SET CACHING (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7e2c9ee878b49065a040865bc32d62837e8b8e25
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781015"
---
# <a name="set-result-set-caching-transact-sql-preview-for-azure-sql-data-warehouse-gen2"></a>SET RESULT SET CACHING (Transact-SQL) (предварительная версия для хранилища данных SQL Azure 2-го поколения)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

При выполнении этой команды Хранилище данных SQL Azure кэширует результирующие наборы запроса.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  

> [!Note]
> Хотя эта функция развертывается во всех регионах, проверьте, какая версия развернута в вашем экземпляре, а также изучите актуальные [заметки о выпуске Хранилища данных SQL Azure](/azure/sql-data-warehouse/release-notes-10-0-10106-0), чтобы узнать о доступности функции.
  
Эта команда должна выполняться при подключении к базе данных master.  Изменение данного параметра базы данных применяется немедленно.  Затраты на хранение связаны с кэшированием результирующих наборов запроса. После отключения кэширования результатов для базы данных ранее сохраненный кэш результатов немедленно удаляется из Хранилища данных SQL Azure. В [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql?view=azure-sqldw-latest) появился новый столбец с именем is_result_set_caching_on. В нем отображаются параметры кэширования результатов для базы данных.  

**ON** указывает, что результирующие наборы запросов, возвращаемые из этой базы данных, будут кэшироваться в Хранилище данных SQL Azure.

**OFF** указывает, что результирующие наборы запросов, возвращаемые из этой базы данных, не будут кэшироваться в Хранилище данных SQL Azure.

Пользователи могут определить, был ли запрос результатов выполнен с попаданием в кэше или промахом кэша, отправив запрос [sys.pdw_request_steps](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql?view=azure-sqldw-latest) с конкретным идентификатором request_id. Если имеет место попадание в кэше, результат запроса будет содержать один шаг со следующими сведениями:

|**Имя столбца**|**Оператор**|**Значение**|
|----|----|----|
|operation_type|=|ReturnOperation|
|step_index|=|0|
|location_type|=|Control|
|command|Похоже|%DWResultCacheDb%|
||||
  
## <a name="permissions"></a>Разрешения

Требуются следующие разрешения:

- имя входа субъекта серверного уровня, созданное процессом подготовки, или
- член роли базы данных dbmanager.

Владелец базы данных не может изменять базу данных, если он не является членом роли dbmanager.
  
## <a name="examples"></a>Примеры

### <a name="enable-result-set-caching-for-a-database"></a>Включение кэширования результирующих наборов для базы данных

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING ON;
```

### <a name="disable-result-set-caching-for-a-database"></a>Выключение кэширования результирующих наборов для базы данных

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING OFF;
```

### <a name="check-result-set-caching-setting-for-a-database"></a>Проверка кэширования результирующих наборов для базы данных

```sql
SELECT name, is_result_set_caching_on  
FROM sys.databases
```

### <a name="check-for-number-of-queries-with-result-set-cache-hit-and-cache-miss"></a>Проверка количества запросов результирующих наборов с попаданием в кэше и промахом кэша

```sql
SELECT  
Queries=CacheHits+CacheMisses,
CacheHits,
CacheMisses,
CacheHitPct=CacheHits*1.0/(CacheHits+CacheMisses)
FROM  
(SELECT  
CacheHits=count(distinct case when s.command like '%DWResultCacheDb%' and
r.resource_class IS NULL and s.operation_type = 'ReturnOperation' and  
s.step_index = 0 then s.request_id else null end) ,
CacheMisses=count(distinct case when r.resource_class IS NOT NULL then  
s.request_id else null end)
     FROM sys.dm_pdw_request_steps s  
     JOIN sys.dm_pdw_exec_requests r  
     ON s.request_id = r.request_id) A
```

### <a name="check-for-result-set-cache-hit-or-cache-miss-for-a-query"></a>Проверка попадания в кэше и промаха кэша результирующих наборов для запроса

```sql
If
(SELECT step_index  
FROM sys.dm_pdw_request_steps  
WHERE request_id = 'QID58286'
      and operation_type = 'ReturnOperation'
      and command like '%DWResultCacheDb%') = 0
SELECT 1 as is_cache_hit  
ELSE
SELECT 0 as is_cache_hit
```

### <a name="check-for-all-queries-with-result-set-cache-hits"></a>Проверка всех запросов с попаданием в кэше результирующих наборов

```sql
SELECT *  
FROM sys.dm_pdw_request_steps  
WHERE command like '%DWResultCacheDb%' and step_index = 0
```

## <a name="see-also"></a>См. также раздел

[Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)</br>
[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)