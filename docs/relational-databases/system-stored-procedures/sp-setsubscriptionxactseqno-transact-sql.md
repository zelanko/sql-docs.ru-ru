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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 60d27260378a8f0d6706b85ea02232ffca6a05c8
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827506"
---
# <a name="sp_setsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется во время устранения неполадок, чтобы указать последнюю доставленную транзакцию с помощью регистрационного номера транзакции в журнале (LSN), что позволяет агент распространения начать доставку в следующую транзакцию. После перезагрузки агент распространения возвращает транзакции, превышающие этот предел (LSN) из кэша базы данных распространителя (msrepl_commands). Эта хранимая процедура выполняется на подписчике в базе данных подписки. Не поддерживается для подписчиков, отличных от подписчика SQL Server.  
  
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
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию. Для издателя, не являющегося SQL Server, *publisher_db* является именем базы данных распространителя.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Если агент распространения совместно используется несколькими публикациями, необходимо указать значение ALL для параметра *publication*.  
  
`[ @xact_seqno = ] xact_seqno`Номер LSN следующей транзакции на распространителе, применяемой на подписчике. *xact_seqno* имеет тип **varbinary (16)** и не имеет значения по умолчанию.  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ORIGINAL XACT_SEQNO**|**varbinary (16)**|Исходный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**UPDATED XACT_SEQNO**|**varbinary (16)**|Обновленный номер LSN следующей транзакции, которая должна быть применена на подписчике.|  
|**SUBSCRIPTION STREAM COUNT**|**int**|Количество потоков подписки, используемых во время последней синхронизации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_setsubscriptionxactseqno** используется в репликации транзакций.  
  
 **sp_setsubscriptionxactseqno** нельзя использовать в одноранговой топологии репликации транзакций.  
  
 **sp_setsubscriptionxactseqno** можно использовать для пропуска определенной транзакции, которая вызывает ошибку при применении на подписчике. При возникновении сбоя и после остановки агент распространения вызовите [sp_helpsubscriptionerrors &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) на распространителе, чтобы получить xact_seqno значение невыполненной транзакции, а затем вызовите **sp_setsubscriptionxactseqno**, передав это значение для *xact_seqno*. Тем самым будет обеспечена обработка только одной команды после этого номера LSN.  
  
 Укажите значение **0** для *xact_seqno* для доставки всех ожидающих команд в базе данных распространителя подписчику.  
  
 **sp_setsubscriptionxactseqno** может завершиться ошибкой, если агент распространения использует потоки с несколькими подписками.  
  
 При возникновении этой ошибки необходимо запустить агент распространителя с потоком одной подписки. Дополнительные сведения см. в статье [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_setsubscriptionxactseqno**.  
  
## <a name="see-more"></a>Еще

[Блог: как пропустить транзакцию](https://repltalk.com/2019/05/28/how-to-skip-a-transaction/)  
