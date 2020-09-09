---
description: sp_showrowreplicainfo (Transact-SQL)
title: sp_showrowreplicainfo (Transact-SQL) | Документация Майкрософт
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5a46fd42c9caa69e808635fc9dcc5125403697a6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543044"
---
# <a name="sp_showrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @ownername = ] 'ownername'` Имя владельца таблицы. *ownerName* имеет тип **sysname**и значение по умолчанию NULL. Этот аргумент полезен для различения таблиц, если база данных содержит несколько таблиц с одним и тем же именем, у каждой из которых свой владелец.  
  
`[ @tablename = ] 'tablename'` Имя таблицы, содержащей строку, для которой возвращаются сведения. *TableName* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @rowguid = ] rowguid` Уникальный идентификатор строки. *rowguid* имеет тип **uniqueidentifier**и не имеет значения по умолчанию.  
  
`[ @show = ] 'show'` Определяет объем данных, возвращаемых в результирующем наборе. параметр *Показывать* имеет тип **nvarchar (20)** и значение по умолчанию. Если **строка**, возвращаются только сведения о версии строки. Если **столбцы**, возвращаются только сведения о версии столбца. Если **оба**значения, возвращаются как сведения о строках, так и о столбцах.  
  
## <a name="result-sets-for-row-information"></a>Результирующие наборы сведений о строках  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Имя сервера, содержащего базу данных с записью о версии строки.|  
|**db_name**|**sysname**|Имя базы данных, содержащей данную запись.|  
|**db_nickname**|**двоичный (6)**|Псевдоним базы данных, содержащей данную запись.|  
|**version**|**int**|Версия записи.|  
|**current_state**|**nvarchar (9)**|Возвращает сведения о текущем состоянии строки.<br /><br /> **y** -строка Data представляет текущее состояние строки.<br /><br /> **n** -строковые данные не представляют текущее состояние строки.<br /><br /> **\<n/a>** — Неприменимо.<br /><br /> **\<unknown>** -Не удается определить текущее состояние.|  
|**rowversion_table**|**nchar (17)**|Указывает, хранятся ли версии строк в таблице [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) или в [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) таблице.|  
|**comment**|**nvarchar(255)**|Дополнительные сведения о данной записи версии строки. Обычно это поле не заполнено.|  
  
## <a name="result-sets-for-column-information"></a>Результирующие наборы сведений о столбце  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_name**|**sysname**|Имя сервера с базой данных, содержащей запись о версии столбца.|  
|**db_name**|**sysname**|Имя базы данных, содержащей данную запись.|  
|**db_nickname**|**двоичный (6)**|Псевдоним базы данных, содержащей данную запись.|  
|**version**|**int**|Версия записи.|  
|**colname**|**sysname**|Имя столбца, представленного данной записью о версии.|  
|**comment**|**nvarchar(255)**|Дополнительные сведения о данной записи версии столбца. Обычно это поле не заполнено.|  
  
## <a name="result-set-for-both"></a>Результирующий набор для значения both  
 Если значение **обоих** параметров выбрано для параметра *Показывать*, возвращаются результирующие наборы строк и столбцов.  
  
## <a name="remarks"></a>Примечания  
 **sp_showrowreplicainfo** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 **sp_showrowreplicainfo** могут быть выполнены только членами предопределенной роли базы данных **db_owner** в базе данных публикации или членами списка доступа к публикации (PAL) в базе данных публикации.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
