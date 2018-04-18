---
title: Хранимая процедура sp_script_synctran_commands (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e8e724f9a787d54f1143472f5823cd5b34962eb4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spscriptsynctrancommands-transact-sql"></a>Хранимая процедура sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Формирует скрипт, который содержит **sp_addsynctrigger** вызовы должны применяться к подписчикам для обновляемых подписок. Имеется один **sp_addsynctrigger** вызова для каждой статьи в публикации. Скрипт также содержит **sp_addqueued_artinfo** вызовы, которые создают **MSsubsciption_articles** таблицы, необходимые для обработки очереди публикаций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication** =] **"***публикации***"**  
 Имя публикации, для которой создается скрипт. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@article** =] **"***статьи***"**  
 Имя статьи, для которой создается скрипт. *статья* — **sysname**, значение по умолчанию **все**, определяющий все статьи включаются в скрипт.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="results-set"></a>Результирующий набор  
 **sp_script_synctran_commands** возвращает результирующий набор, состоящий из одного **nvarchar(4000)** столбца. Результирующий набор формирует полные скрипты необходимые для создания **sp_addsynctrigger** и **sp_addqueued_artinfo** вызовы должны применяться к подписчикам.  
  
## <a name="remarks"></a>Замечания  
 **sp_script_synctran_commands** используется в моментальных снимков и репликации транзакций.  
  
 **sp_addqueued_artinfo** используется для очереди обновляемых подписок.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
