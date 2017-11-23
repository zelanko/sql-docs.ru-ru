---
title: "sp_setsubscriptionxactseqno (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords: sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aab7bf1c5fb7653f4b61af1912af7de3454bf776
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется во время диагностики для задания регистрационного номера следующей транзакции в журнале, подлежащей применению агентом распространителя на подписчике, что позволяет агенту пропустить транзакцию, вызвавшую сбой. Эта хранимая процедура выполняется на подписчике в базе данных подписки. Не поддерживается для подписчиков, отличных от подписчика SQL Server.  
  
> [!CAUTION]  
>  Неверное использование этой хранимой процедуры или задание неправильного номера LSN может привести к тому, что агент распространителя отменит изменения, уже примененные на подписчике, или пропустит все оставшиеся изменения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=** ] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию. Для SQL Server издателем, *publisher_db* имя базы данных распространителя.  
  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Если агент распространителя является общим для нескольких публикаций, необходимо указать значение всех для *публикации*.  
  
 [  **@xact_seqno=** ] *xact_seqno*  
 Номер LSN следующей транзакции на распространителе, которая должна быть применена на подписчике. *xact_seqno* — **varbinary(16)**, не имеет значения по умолчанию.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ИСХОДНЫЙ XACT_SEQNO**|**varbinary(16)**|Исходный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**ОБНОВЛЕННЫЕ XACT_SEQNO**|**varbinary(16)**|Обновленный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**ЧИСЛО ПОТОКА ПОДПИСКИ**|**int**|Количество потоков подписки, используемых во время последней синхронизации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_setsubscriptionxactseqno** используется в репликации транзакций.  
  
 **sp_setsubscriptionxactseqno** не может использоваться в топологии репликации транзакций для коллег.  
  
 **sp_setsubscriptionxactseqno** может использоваться для пропуска определенной транзакции, вызывающей ошибку при применении на подписчике. Если происходит сбой, и после остановки агента распространителя, вызовите [sp_helpsubscriptionerrors &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) на распространителе для получения значения xact_seqno поврежденной транзакции, а затем вызвать **sp_setsubscriptionxactseqno**, передав это значение для *xact_seqno*. Тем самым будет обеспечена обработка только одной команды после этого номера LSN.  
  
 Укажите значение **0** для *xact_seqno* для доставки всех ожидающих применения команд в базе данных распространителя на подписчик.  
  
 **sp_setsubscriptionxactseqno** может завершиться ошибкой, если агент распространителя использует потоки нескольких подписок.  
  
 При возникновении этой ошибки необходимо запустить агент распространителя с потоком одной подписки. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_setsubscriptionxactseqno**.  
  
  
