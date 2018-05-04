---
title: sp_dropanonymousagent (Transact-SQL) | Документы Microsoft
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
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f9e7a1f68199367f2f40716b2295452eb2725a53
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет анонимный агент монитора репликаций на распространителе от издателя. Эта хранимая процедура выполняется на подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@subid=**] *sub_id*  
 Глобальный идентификатор для анонимной подписки. *sub_id* — **uniqueidentifier**, не имеет значения по умолчанию. Этот идентификатор можно получить на подписчике с помощью **sp_helppullsubscription**. Значение в **subid** поле возвращенного результирующего набора будет глобальный идентификатор.  
  
 [  **@type=**] *типа*  
 Тип подписки. *Тип* — **int**, не имеет значения по умолчанию. Допустимые значения: **1** или **2**. Укажите **1**, если в репликации моментальных снимков или репликации транзакций с помощью агента распространителя. Укажите **2**при репликации слиянием с использованием агента слияния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_dropanonymousagent** используется во всех типах репликации.  
  
 Эта хранимая процедура используется только для удаления агентов анонимных подписок и не может быть использована для удаления известных подписок.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **db_owner** предопределенной роли базы данных в базе данных распространителя могут выполнять процедуру **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
