---
title: "GET_TRANSMISSION_STATUS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATUS_TSQL
- TRANSMISSION
- TRANSMISSION_TSQL
- GET_TRANSMISSION_STATUS
- STATUS
- GET_TRANSMISSION_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], transmission status
- Service Broker errors, transmission status
- transmission status information
- status information [SQL Server], conversations
- GET_TRANSMISSION_STATUS statement
ms.assetid: 621805d5-49ed-4764-b3cb-2ae4a3bf797e
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6d5152cca3f4ddb1afe0d8042c84743c31abf9b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="gettransmissionstatus-transact-sql"></a>GET_TRANSMISSION_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает состояние последней передачи для одной стороны диалога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GET_TRANSMISSION_STATUS ( conversation_handle )  
```  
  
## <a name="arguments"></a>Аргументы  
 *conversation_id*  
 Дескриптор диалога для диалога. Этот параметр имеет тип **uniqueidentifier**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nchar**  
  
## <a name="remarks"></a>Замечания  
 Возвращает строку, описывающую состояние последней попытки передачи, для конкретного диалога. Возвращает пустую строку, если последняя попытка передачи завершилась успешно, если было предпринято ни одной попытки передачи или *conversation_handle* не существует.  
  
 Данные, возвращаемые этой функцией, совпадают с данными, отображаемыми в столбце last_transmission_error представления управления sys.transmission_queue. Однако эта функция может быть использована для нахождения состояния передачи диалогов, у которых на данный момент нет сообщений в очереди передачи.  
  
> [!NOTE]  
>  GET_TRANSMISSION_STATUS не предоставляет сведения для сообщений, у которых нет конечной точки диалога в текущем экземпляре. Поэтому нет доступных сведений для перенаправляемых сообщений.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о состоянии передачи для диалога с помощью дескриптора диалога `58ef1d2d-c405-42eb-a762-23ff320bddf0`.  
  
```  
SELECT Status =  
    GET_TRANSMISSION_STATUS('58ef1d2d-c405-42eb-a762-23ff320bddf0') ;  
```  
  
 Далее приведен образец результирующего набора, отредактированного по длине строк:  
  
 `Status`  
  
 `-------------------------------`  
  
 `The Service Broker protocol transport is disabled or not configured.`  
  
 В этом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не настроен для поддержки [!INCLUDE[ssSB](../../includes/sssb-md.md)] для обмена данными по сети.  
  
## <a name="see-also"></a>См. также:  
 [sys.conversation_endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)   
 [sys.transmission_queue &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  

