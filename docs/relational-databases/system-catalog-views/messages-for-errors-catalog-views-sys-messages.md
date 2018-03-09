---
title: "sys.messages (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b8163fb44e72942422b044a23687c395a75bbfcd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Представления каталога сообщений (для ошибок) - sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого **message_id** или **language_id** сообщения об ошибках в системе, как системные и определяемые пользователем сообщения. Дополнительные сведения см. в разделе [sp_addmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|Идентификатор сообщения. Уникален в пределах сервера. Сообщения с идентификаторами, меньшими 50000, являются системными.|  
|**language_id**|**smallint**|Идентификатор языка, для которого текст в **текст** используется, как определено в **syslanguages**. Он уникален для указанного **message_id**.|  
|**Серьезность**|**tinyint**|Степень серьезности сообщения, от 1 до 25. Это то же самое для всех языков сообщения в пределах **message_id**.|  
|**is_event_logged**|**bit**|1 = сообщение заносится в журнал событий при возникновении ошибки. Это то же самое для всех языков сообщения в пределах **message_id**.|  
|**text**|**nvarchar(2048)**|Текст сообщения, используемого при соответствующих **language_id** активен.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [THROW &#40; Transact-SQL &#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [&#40; сообщения для ошибок &#41; Представления каталога &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Сообщение об исключении программирование окон](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [События и ошибки ядра СУБД](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
