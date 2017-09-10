---
title: "KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c6937424d2cd68095952c3faba2a446488e9122
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет подписки на уведомления о запросах из экземпляра. С помощью этой инструкции можно удалить определенную подписку или все подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
KILL QUERY NOTIFICATION SUBSCRIPTION   
   { ALL | subscription_id }  
```  
  
## <a name="arguments"></a>Аргументы  
 ALL  
 Удаляет все подписки экземпляра.  
  
 *ИД_ПОДПИСКИ*  
 Удаляет подписку с ИД подписки *ИД_ПОДПИСКИ*.  
  
## <a name="remarks"></a>Замечания  
 Инструкция KILL QUERY NOTIFICATION SUBSCRIPTION удаляет подписки на уведомления о запросах без выдачи сообщения-уведомления.  
  
 *ИД_ПОДПИСКИ* представляет идентификатор подписки, отображаемый в динамическом административном представлении [sys.dm_qn_subscriptions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 Если указанного идентификатора подписки не существует, инструкция возвращает ошибку.  
  
## <a name="permissions"></a>Permissions  
 Разрешение на выполнение этой инструкции ограничено членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-removing-all-query-notification-subscriptions-in-the-instance"></a>A. Удаление всех подписок на уведомления о запросах из экземпляра  
 В следующем с экземпляра удаляются все подписки на уведомления о запросах.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION ALL ;  
```  
  
### <a name="b-removing-a-single-query-notification-subscription"></a>Б. Удаление отдельной подписки на уведомления о запросах  
 В следующем примере удаляется подписка на уведомления о запросах с идентификатором `73`.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION 73 ;  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_qn_subscriptions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  

