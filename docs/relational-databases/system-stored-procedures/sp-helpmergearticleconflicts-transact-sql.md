---
title: sp_helpmergearticleconflicts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85e75e1ce52866eb04b3c410f021db8de392239a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122330"
---
# <a name="sp_helpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
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
`[ @publication = ] 'publication'`Имя публикации слиянием. Аргумент *publication* имеет тип **sysname**и значение по **%** умолчанию, которое возвращает все статьи в базе данных с конфликтами.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных издателя. Аргумент *publisher_db* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**рассмотрен**|**sysname**|Имя статьи.|  
|**source_owner**|**sysname**|Владелец исходного объекта.|  
|**source_object**|**nvarchar (386)**|Имя исходного объекта.|  
|**conflict_table**|**nvarchar(258)**|Имя таблицы, хранящей конфликты при операциях вставки или обновления.|  
|**guidcolname**|**sysname**|Имя RowGuidCol для исходного объекта.|  
|**centralized_conflicts**|**int**|Указывает, хранятся ли конфликтные записи на заданном издателе.|  
  
 Если статья содержит только конфликты удаления и **conflict_table** строк, то имя **conflict_table** в результирующем наборе будет иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpmergearticleconflicts** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
