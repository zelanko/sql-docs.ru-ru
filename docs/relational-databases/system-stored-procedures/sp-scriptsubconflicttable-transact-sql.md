---
title: sp_scriptsubconflicttable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptsubconflicttable
- sp_scriptsubconflicttable_TSQL
helpviewer_keywords:
- sp_scriptsubconflicttable
ms.assetid: 13867145-3dad-47a4-8d50-a65175418479
author: stevestein
ms.author: sstein
ms.openlocfilehash: 806209b4f881576c680c14b0bc17ec4fd04a086c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126372"
---
# <a name="spscriptsubconflicttable-transact-sql"></a>sp_scriptsubconflicttable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает скрипт для создания таблицы конфликтов на подписчике для заданной статьи очереди подписок. Созданный скрипт выполняется на подписчике в базе данных подписки. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_scriptsubconflicttable [@publication =] 'publication'    , [@article =] 'article'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, которая содержит статью. В базе данных это имя должно быть уникальным. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи подписки. *статья* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cmdtext**|**nvarchar(4000)**|Возвращает скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания таблицы конфликтов на подписчике для статьи очереди подписок. Этот скрипт выполняется на подписчике в базе данных подписки.|  
  
## <a name="remarks"></a>Примечания  
 **sp_scriptsubconflicttable** используется для подписчиков, имеющих подписки, где исходный моментальный снимок применяется вручную. Таблица конфликтов является дополнительной таблицей на подписчике.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_scriptsubconflicttable**.  
  
## <a name="see-also"></a>См. также  
 [Обнаружение и разрешение конфликтов обновлений посредством очередей](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
