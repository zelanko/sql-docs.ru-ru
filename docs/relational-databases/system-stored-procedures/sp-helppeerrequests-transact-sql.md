---
description: sp_helppeerrequests (Transact-SQL)
title: sp_helppeerrequests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b16e7c25ebc47ccdb97950658de11d738a0d1666
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485956"
---
# <a name="sp_helppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения обо всех запросах состояния, полученных участниками в топологии одноранговой репликации, где эти запросы были инициированы путем запуска [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) в любой опубликованной базе данных в топологии. Эта хранимая процедура выполняется в базе данных публикации при участии издателя в топологии одноранговой репликации. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации в одноранговой топологии, для которой были отправлены запросы состояния. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @description = ] 'description'` Значение, которое может быть использовано для определения отдельных запросов состояния, что позволяет фильтровать возвращенные ответы на основе определяемых пользователем сведений, полученных при вызове [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Description* имеет тип **nvarchar (4000)** и значение по умолчанию **%** . По умолчанию возвращается информация обо всех запросах состояния публикации. Этот параметр используется для возврата только запросов состояния с описанием, совпадающим со значением, указанным в *описании*, где символьные строки сопоставляются с помощью предложения [Like &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md) .  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор запроса.|  
|**публикации**|**sysname**|Имя публикации, запрос состояния которой был отправлен.|  
|**sent_date**|**datetime**|Дата и время отправления запроса состояния.|  
|**description**|**nvarchar(4000)**|Пользовательская информация, которую можно использовать для идентификации запросов состояния.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_helppeerrequests** используется в одноранговой репликации транзакций.  
  
 **sp_helppeerrequests** используется при восстановлении базы данных, опубликованной в одноранговой топологии.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_helppeerrequests**.  
  
## <a name="see-also"></a>См. также  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
