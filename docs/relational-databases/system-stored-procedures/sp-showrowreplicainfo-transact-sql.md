---
title: sp_showrowreplicainfo (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87857390035273ca2350f90175cc4254f182bb7c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spshowrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о строке в таблице, которая используется как статья в репликации слиянием. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@ownername**=] **"***ownername***"**  
 Имя владельца таблицы. *ownername* — **sysname**, значение по умолчанию NULL. Этот аргумент полезен для различения таблиц, если база данных содержит несколько таблиц с одним и тем же именем, у каждой из которых свой владелец.  
  
 [  **@tablename =**] **"***tablename***"**  
 Имя таблицы, содержащей строку, сведения о которой будут возвращены. *TableName* — **sysname**, значение по умолчанию NULL.  
  
 [  **@rowguid =**] *rowguid*  
 Уникальный идентификатор строки. *ROWGUID* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
 [ **@show**=] **"***Показать***"**  
 Определяет объем сведений, возвращаемых в составе набора результатов. *Показать* — **nvarchar(20)** и по умолчанию BOTH. Если **строки**, возвращаются только сведения о версии строки. Если **столбцы**, возвращаются только сведения о версии столбца. Если **оба**и строк, и возвращаются сведения о столбцах.  
  
## <a name="result-sets-for-row-information"></a>Результирующие наборы сведений о строках  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Имя сервера, содержащего базу данных с записью о версии строки.|  
|**db_name**|**sysname**|Имя базы данных, содержащей данную запись.|  
|**db_nickname**|**binary(6)**|Псевдоним базы данных, содержащей данную запись.|  
|**version**|**int**|Версия записи.|  
|**current_state**|**nvarchar(9)**|Возвращает сведения о текущем состоянии строки.<br /><br /> **y** — данные строки представляют ее текущее состояние строки.<br /><br /> **n** -данные строки не представляют ее текущее состояние строки.<br /><br /> **\<н/д >** — неприменимо.<br /><br /> **\<Неизвестный >** -не удается определить текущее состояние.|  
|**rowversion_table**|**nchar(17)**|Указывает, хранятся ли версии строк в [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) таблицы или [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) таблицы.|  
|**Комментарий**|**nvarchar(255)**|Дополнительные сведения о данной записи версии строки. Обычно это поле не заполнено.|  
  
## <a name="result-sets-for-column-information"></a>Результирующие наборы сведений о столбце  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Имя сервера с базой данных, содержащей запись о версии столбца.|  
|**db_name**|**sysname**|Имя базы данных, содержащей данную запись.|  
|**db_nickname**|**binary(6)**|Псевдоним базы данных, содержащей данную запись.|  
|**version**|**int**|Версия записи.|  
|**colname**|**sysname**|Имя столбца, представленного данной записью о версии.|  
|**Комментарий**|**nvarchar(255)**|Дополнительные сведения о данной записи версии столбца. Обычно это поле не заполнено.|  
  
## <a name="result-set-for-both"></a>Результирующий набор для значения both  
 Если значение **оба** выбирается для *Показать*, то возвращается столбцов и строк результирующих наборов.  
  
## <a name="remarks"></a>Замечания  
 **sp_showrowreplicainfo** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 **sp_showrowreplicainfo** может быть выполнена только членами **db_owner** предопределенной роли базы данных в базе данных публикации, а также члены списка доступа публикации (PAL) в базе данных публикации.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
