---
title: sp_replication_agent_checkup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replication_agent_checkup_TSQL
- sp_replication_agent_checkup
helpviewer_keywords:
- sp_replication_agent_checkup
ms.assetid: 50357c2e-71aa-4e13-9e2e-0977a3655cc9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 15d226e20448e503344667ed801bdbd9b7cb07f9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950718"
---
# <a name="spreplicationagentcheckup-transact-sql"></a>sp_replication_agent_checkup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет каждую базу данных распространителя на наличие агентов репликации, которые выполняются, но не записывали сведения в журнал в пределах указанного тактового импульса. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replication_agent_checkup [ [ @heartbeat_interval = ] heartbeat_interval ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @heartbeat_interval = ] 'heartbeat_interval'` — Максимальное количество минут, в которых агент может выполняться без ведения журнала сообщений о ходе выполнения. *heartbeat_interval* — **int**, значение по умолчанию 10 минут.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **sp_replication_agent_checkup** выдает ошибку 14151 для каждого агента, он обнаруживает как подозрительная. Она также записывает сообщение об агентах в журнал ошибок.  
  
## <a name="remarks"></a>Примечания  
 **sp_replication_agent_checkup** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_replication_agent_checkup**.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
