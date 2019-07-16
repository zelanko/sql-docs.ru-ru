---
title: хранимой процедуре sp_showrowreplicainfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords:
- sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0c750fd35dce98c1d754f192214cd96cfc56143
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032892"
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
`[ @ownername = ] 'ownername'` — Имя владельца таблицы. *ownername* — **sysname**, значение по умолчанию NULL. Этот аргумент полезен для различения таблиц, если база данных содержит несколько таблиц с одним и тем же именем, у каждой из которых свой владелец.  
  
`[ @tablename = ] 'tablename'` — Имя таблицы, которая содержит по строке, для которого возвращаются данные. *TableName* — **sysname**, значение по умолчанию NULL.  
  
`[ @rowguid = ] rowguid` — Уникальный идентификатор строки. *ROWGUID* — **uniqueidentifier**, не имеет значения по умолчанию.  
  
`[ @show = ] 'show'` Определяет объем сведений, возвращаемых в результирующем наборе. *Показать* — **nvarchar(20)** значение по умолчанию ОБА. Если **строки**, возвращается только сведения о версии строки. Если **столбцы**, возвращается только сведения о версии столбца. Если **оба**, и строк, и возвращаются сведения о столбцах.  
  
## <a name="result-sets-for-row-information"></a>Результирующие наборы сведений о строках  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Имя сервера, содержащего базу данных с записью о версии строки.|  
|**db_name**|**sysname**|Имя базы данных, содержащей данную запись.|  
|**db_nickname**|**binary(6)**|Псевдоним базы данных, содержащей данную запись.|  
|**version**|**int**|Версия записи.|  
|**параметр current_state со значением**|**nvarchar(9)**|Возвращает сведения о текущем состоянии строки.<br /><br /> **y** — данные строки представляют ее текущее состояние строки.<br /><br /> **n** -данных в строке не представляет текущее состояние строки.<br /><br /> **\<н/д >** — неприменимо.<br /><br /> **\<Неизвестный >** -не удается определить текущее состояние.|  
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
 Если значение **оба** будет автоматически выбран *Показать*, то возвращается номер строки и столбца результирующих наборов.  
  
## <a name="remarks"></a>Примечания  
 **хранимой процедуре sp_showrowreplicainfo** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 **хранимой процедуре sp_showrowreplicainfo** может быть выполнена только членами **db_owner** предопределенной роли базы данных в базе данных публикации или участники списка доступа публикации (PAL) в базе данных публикации.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
