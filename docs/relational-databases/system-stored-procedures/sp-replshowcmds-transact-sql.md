---
title: sp_replshowcmds (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 74526c46a3758829a89c71d41c071070ec907d5f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, отмеченных для репликации, в удобочитаемом формате. **sp_replshowcmds** можно выполнять только тогда, когда клиентские подключения (а также текущее подключение) не считывают реплицированные транзакции из журнала. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@maxtrans** =] *maxtrans*  
 Число транзакций, сведения о которых необходимо возвратить. *maxtrans* — **int**, значение по умолчанию **1**, которое указывает максимальное число транзакций, ожидающих репликации, для которой **sp_replshowcmds** Возвращает сведения.  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_replshowcmds** — это диагностическая процедура, которая возвращает сведения о базе данных публикации, из которого выполняется.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|Последовательный номер команды.|  
|**originator_id**|**int**|Идентификатор инициатора команды всегда **0**.|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя, всегда **0**.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**команда**|**nvarchar(1024)**|Команда языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="remarks"></a>Замечания  
 **sp_replshowcmds** используется в репликации транзакций.  
  
 С помощью **sp_replshowcmds**, можно просмотреть транзакции, которые в текущий момент не распределенные (транзакции, остающиеся в журнале транзакций, не были отправлены распространителю).  
  
 Клиенты, использующие **sp_replshowcmds** и **sp_replcmds** в той же базе данных, получают ошибку 18752.  
  
 Во избежание этой ошибки первый клиент должен либо отключиться или роль клиента как агент чтения журнала должен освободить с помощью процедуры **sp_replflush**. После отключения всех клиентов из средства чтения журнала **sp_replshowcmds** для успешного выполнения.  
  
> [!NOTE]  
>  **sp_replshowcmds** следует запускать только в целях устранения неполадок с репликацией.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_replshowcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
