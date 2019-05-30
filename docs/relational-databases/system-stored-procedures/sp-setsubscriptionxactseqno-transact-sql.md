---
title: sp_setsubscriptionxactseqno (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9b6f9426d4381f33d529e1efefa8afd6a1fc44b
ms.sourcegitcommit: 9388dcccd6b89826dde47b4c05db71274cfb439a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270157"
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется во время устранения неполадок для указания последней доставленной транзакции с помощью последовательности номер транзакции в журнале (LSN), что агент распространителя начать предоставления в следующей транзакции. При перезапуске, агент распространителя возвращает транзакций больше водяного знака (LSN) из кэша базы данных распространителя (msrepl_commands). Эта хранимая процедура выполняется на подписчике в базе данных подписки. Не поддерживается для подписчиков, отличных от подписчика SQL Server.  
  
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
`[ @publisher = ] 'publisher'` — Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'` — Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию. Для SQL Server издателем, *publisher_db* — имя базы данных распространителя.  
  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Если агент распространителя является общим для нескольких публикаций, необходимо указать значение ALL для *публикации*.  
  
`[ @xact_seqno = ] xact_seqno` — Это номер LSN следующей транзакции на распространителе, чтобы применить на подписчике. *xact_seqno* — **varbinary(16)**, не имеет значения по умолчанию.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ORIGINAL XACT_SEQNO**|**varbinary(16)**|Исходный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**UPDATED XACT_SEQNO**|**varbinary(16)**|Обновленный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**ЧИСЛО ПОТОКА ПОДПИСКИ**|**int**|Количество потоков подписки, используемых во время последней синхронизации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_setsubscriptionxactseqno** используется в репликации транзакций.  
  
 **sp_setsubscriptionxactseqno** не может использоваться в топологии репликации транзакций peer-to-peer.  
  
 **sp_setsubscriptionxactseqno** может использоваться для пропуска определенной транзакции, вызывающей ошибку при применении на подписчике. При сбое, а также после остановки агента распространителя, вызовите [sp_helpsubscriptionerrors &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) на распространителе для получения значения xact_seqno поврежденной транзакции, а затем вызовите **sp_setsubscriptionxactseqno**, передав это значение для *xact_seqno*. Тем самым будет обеспечена обработка только одной команды после этого номера LSN.  
  
 Укажите значение **0** для *xact_seqno* для доставки всех ожидающих применения команд в базе данных распространителя к подписчику.  
  
 **sp_setsubscriptionxactseqno** может завершиться ошибкой, если агент распространителя использует потоки нескольких подписок.  
  
 При возникновении этой ошибки необходимо запустить агент распространителя с потоком одной подписки. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_setsubscriptionxactseqno**.  
  
## <a name="see-more"></a>Подробнее

[Блог: Пропуск транзакции](https://repltalk.com/2019/05/28/how-to-skip-a-transaction/)  
