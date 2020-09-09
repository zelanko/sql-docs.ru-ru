---
description: sp_dropmergefilter (Transact-SQL)
title: sp_dropmergefilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 238ef7b0c8a6c56aff5a034f192dd48298cf0fa1
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536550"
---
# <a name="sp_dropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет фильтр слияния. **sp_dropmergefilter** удаляет все столбцы фильтра слияния, определенные для удаляемого фильтра слияния. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @filtername = ] 'filtername'` Имя удаляемого фильтра. *filtername* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` Включает или отключает возможность недействительности моментального снимка. *force_invalidate_snapshot* является **битом**и имеет значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье слияния не приводят к недействительности моментального снимка.  
  
 **1** означает, что изменения в статье слияния могут привести к недействительности моментального снимка. Если это так, значение **1** дает разрешение на создание нового моментального снимка.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` Включает или отключает возможность пометить подписку как недопустимую. *force_reinit_subscription* является **битом**и имеет значение по умолчанию **0**.  
  
 значение **0** указывает, что изменения в фильтре статей публикации не приводят к недопустимым подпискам.  
  
 **1** означает, что изменения в фильтре статей публикации приводят к недействительности подписок.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropmergefilter** используется в репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_dropmergefilter**.  
  
## <a name="see-also"></a>См. также:  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
