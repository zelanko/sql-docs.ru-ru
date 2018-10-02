---
title: KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7ba34906f9ff4b2595644d16b2c13ea3b8a63269
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713162"
---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
 *subscription_id*  
 Удаляет подписку с идентификатором *subscription_id*.  
  
## <a name="remarks"></a>Remarks  
 Инструкция KILL QUERY NOTIFICATION SUBSCRIPTION удаляет подписки на уведомления о запросах без выдачи сообщения-уведомления.  
  
 Аргумент *subscription_id* представляет собой идентификатор подписки, отображаемый в динамическом административном представлении [sys.dm_qn_subscriptions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 Если указанного идентификатора подписки не существует, инструкция возвращает ошибку.  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на выполнение этой инструкции ограничено членами предопределенной роли сервера **sysadmin**.  
  
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
 [sys.dm_qn_subscriptions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
