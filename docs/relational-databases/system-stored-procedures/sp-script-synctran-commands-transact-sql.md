---
title: sp_script_synctran_commands (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9ee35eb4c5d67ff50f4f08c1cfa29596e27aec2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536182"
---
# <a name="spscriptsynctrancommands-transact-sql"></a>Хранимая процедура sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Формирует скрипт, который содержит **sp_addsynctrigger** вызовы должны применяться к подписчикам для обновляемых подписок. Имеется один **sp_addsynctrigger** вызовите для каждой статьи в публикации. Скрипт также содержит **sp_addqueued_artinfo** вызовы, которые создают **MSsubsciption_articles** таблицы, необходимые для обработки очереди публикаций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации, для которой создается сценарий. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @article = ] 'article'` — Имя статьи для включения в скрипт. *статья* — **sysname**, значение по умолчанию **все**, которое указывает, все статьи включаются в скрипт.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="results-set"></a>Результирующий набор  
 **sp_script_synctran_commands** возвращает результирующий набор, состоящий из одного **nvarchar(4000)** столбца. Результирующий набор формирует полные скрипты необходимые для создания **sp_addsynctrigger** и **sp_addqueued_artinfo** вызовы на подписчиках.  
  
## <a name="remarks"></a>Примечания  
 **sp_script_synctran_commands** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_addqueued_artinfo** используется для очереди обновляемых подписок.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>См. также  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
