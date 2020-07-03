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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9ab3528c496722877310c13d073158bd20969bc4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85861774"
---
# <a name="sp_deletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет строки из таблицы конфликтов или [MSmerge_conflicts_info &#40;таблицы&#41;Transact-SQL](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) . Эта хранимая процедура выполняется на компьютере, где хранится таблица конфликта, в любой базе данных.  
  
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
`[ @conflict_table = ] 'conflict_table'`Имя таблицы конфликтов. Аргумент *conflict_table* имеет тип **sysname**и значение по умолчанию **%** . Если *conflict_table* указан как null или **%** , конфликт предполагается как конфликт удаления, а строка, соответствующая *rowguid* и *origin_datasource* , и *Source_object* удаляется из [&#40;таблицы MSmerge_conflicts_info&#41;Transact-SQL](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) .  
  
`[ @source_object = ] 'source_object'`Имя исходной таблицы. *source_object* имеет тип **nvarchar (386)** и значение по умолчанию NULL.  
  
`[ @rowguid = ] 'rowguid'`Идентификатор строки для конфликта удаления. *rowguid* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
`[ @origin_datasource = ] 'origin_datasource'`Источник конфликта. *origin_datasource* имеет тип **varchar (255)** и не имеет значения по умолчанию.  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'`Флаг, указывающий, что *conflict_table* должен быть удален, если пуст. *drop_table_if_empty* имеет тип **varchar (10)** и значение по умолчанию false.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_deletemergeconflictrow** используется в репликации слиянием.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41;ная](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) таблица является системной таблицей и не удаляется из базы данных, даже если она пуста.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
