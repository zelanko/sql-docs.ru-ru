---
title: sp_helpmergearticleconflicts (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5fcecf6d7fe755ecf8eac2acb21cbe225b4ec747
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает конфликтные статьи публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации или на подписчике в базе данных подписки слиянием.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 — Имя публикации слиянием. *публикации* — **sysname**, значение по умолчанию **%**, который возвращает все статьи в базе данных, содержащие конфликты.  
  
 [  **@publisher=**] **"***издатель***"**  
 — Это имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 — Это имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию NULL.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**В статье**|**sysname**|Имя статьи.|  
|**source_owner**|**sysname**|Владелец исходного объекта.|  
|**source_object**|**nvarchar(386)**|Имя исходного объекта.|  
|**conflict_table**|**nvarchar(258)**|Имя таблицы, хранящей конфликты при операциях вставки или обновления.|  
|**guidcolname**|**sysname**|Имя RowGuidCol для исходного объекта.|  
|**centralized_conflicts**|**int**|Указывает, хранятся ли конфликтные записи на заданном издателе.|  
  
 Если у статьи есть только конфликты удаления и нет **conflict_table** строк, имя **conflict_table** в результирующем наборе содержит значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpmergearticleconflicts** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
