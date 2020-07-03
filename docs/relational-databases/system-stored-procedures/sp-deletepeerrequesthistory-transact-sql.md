---
title: sp_deletepeerrequesthistory (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fe3a7edbb00eb7d3a4da1aa78689685a54e56277
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85861420"
---
# <a name="sp_deletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет журнал, связанный с запросом состояния публикации, который включает журнал запросов ([MSpeer_request &#40;Transact-sql&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)), а также журнал ответов ([MSpeer_response &#40;transact-SQL&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)). Эта хранимая процедура выполняется в базе данных публикации на издателе, участвующем в топологии одноранговой репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, для которой был сделан запрос состояния. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @request_id = ] request_id`Указывает отдельный запрос состояния, чтобы все ответы на этот запрос удалялись. *request_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @cutoff_date = ] cutoff_date`Указывает дату прекращения, до которой удаляются все предыдущие записи ответа. *cutoff_date* имеет тип **DateTime**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_deletepeerrequesthistory** используется в одноранговой топологии репликации транзакций. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 При выполнении **sp_deletepeerrequesthistory**необходимо указать либо *request_id* , либо *cutoff_date* .  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_deletepeerrequesthistory**.  
  
## <a name="see-also"></a>См. также  
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
