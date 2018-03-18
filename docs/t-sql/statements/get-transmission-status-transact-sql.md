---
title: "GET_TRANSMISSION_STATUS (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ef506faa6df757ac3a1a89af5b1d1b0715e33fd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="gettransmissionstatus-transact-sql"></a>GET_TRANSMISSION_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает состояние последней передачи для одной стороны диалога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GET_TRANSMISSION_STATUS ( conversation_handle )  
```  
  
## <a name="arguments"></a>Аргументы  
 *conversation_id*  
 Дескриптор диалога для диалога. Этот параметр имеет тип **uniqueidentifier**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nchar**  
  
## <a name="remarks"></a>Примечания  
 Возвращает строку, описывающую состояние последней попытки передачи, для конкретного диалога. Возвращает пустую строку, если последняя попытка передачи завершилась успешно, если не было предпринято ни одной попытки передачи или если аргумент *conversation_handle* не существует.  
  
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
  
 ```
 Status  
 ------------------------------- 
 The Service Broker protocol transport is disabled or not configured.
 ```  
  
 В этом случае компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не был настроен для разрешения [!INCLUDE[ssSB](../../includes/sssb-md.md)] обмениваться данными по сети.  
  
## <a name="see-also"></a>См. также  
 [sys.conversation_endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)   
 [sys.transmission_queue (Transact-SQL)](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  
