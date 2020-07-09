---
title: GET_TRANSMISSION_STATUS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f1730fac109d23211fedcccec8603a7129adf7ad
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899162"
---
# <a name="get_transmission_status-transact-sql"></a>GET_TRANSMISSION_STATUS (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

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
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [sys.conversation_endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)   
 [sys.transmission_queue (Transact-SQL)](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  
