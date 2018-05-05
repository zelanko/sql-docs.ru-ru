---
title: sys.messages (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: aa37a19743801bea70b1c78d8c9606be74dfe2f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Представления каталога сообщений (для ошибок) - sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого **message_id** или **language_id** сообщения об ошибках в системе, как системные и определяемые пользователем сообщения. Дополнительные сведения см. в разделе [sp_addmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|Идентификатор сообщения. Уникален в пределах сервера. Сообщения с идентификаторами, меньшими 50000, являются системными.|  
|**language_id**|**smallint**|Идентификатор языка, для которого текст в **текст** используется, как определено в **syslanguages**. Он уникален для указанного **message_id**.|  
|**severity**|**tinyint**|Степень серьезности сообщения, от 1 до 25. Это то же самое для всех языков сообщения в пределах **message_id**.|  
|**is_event_logged**|**бит**|1 = сообщение заносится в журнал событий при возникновении ошибки. Это то же самое для всех языков сообщения в пределах **message_id**.|  
|**text**|**nvarchar(2048)**|Текст сообщения, используемого при соответствующих **language_id** активен.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [THROW (Transact-SQL)](../../t-sql/language-elements/throw-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Сообщения &#40;ошибок&#41; представления каталога &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Сообщение об исключении программирование окон](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [События и ошибки компонента Database Engine](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
