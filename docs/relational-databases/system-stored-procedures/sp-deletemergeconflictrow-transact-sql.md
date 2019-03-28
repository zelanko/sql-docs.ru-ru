---
title: sp_deletemergeconflictrow (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5bef3e4902562edde0adb2a4f495c51e6a82b091
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535286"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет строки из таблицы конфликта или [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) таблицы. Эта хранимая процедура выполняется на компьютере, где хранится таблица конфликта, в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @conflict_table = ] 'conflict_table'` — Имя таблицы конфликтов. *conflict_table* — **sysname**, значение по умолчанию **%**. Если *conflict_table* указан как NULL или **%**, конфликт считается конфликтом удаления и строка, совпадающая *rowguid* и *origin_datasource* и *source_object* удаляется из [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) таблицы.  
  
`[ @source_object = ] 'source_object'` — Имя исходной таблицы. *source_object* — **nvarchar(386)**, значение по умолчанию NULL.  
  
`[ @rowguid = ] 'rowguid'` — Это идентификатор строки для конфликта удаления. *ROWGUID* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
`[ @origin_datasource = ] 'origin_datasource'` Происхождение конфликта. *origin_datasource* — **varchar(255)**, не имеет значения по умолчанию.  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'` Флаг, указывающий, что *conflict_table* , удалена, если пусто. *drop_table_if_empty* — **varchar(10)**, значение по умолчанию FALSE.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_deletemergeconflictrow** используется в репликации слиянием.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) таблица является системной таблицей и не удаляется из базы данных, даже если она пуста.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
