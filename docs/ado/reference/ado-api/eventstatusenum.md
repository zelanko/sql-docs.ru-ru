---
title: "EventStatusEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: EventStatusEnum
helpviewer_keywords: EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 82518cbfd6572f03cbe0b742b52bb5e4acd3d8e9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="eventstatusenum"></a>EventStatusEnum
Указывает текущее состояние выполнения события.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|Запрашивает отмену операции, которая вызвала возникновения события.|  
|**adStatusCantDeny**|3|Указывает, что операция не может запрашивать отмену отложенной операции.|  
|**adStatusErrorsOccurred**|2|Указывает на сбой операции, которая вызвала событие из-за ошибки или ошибки.|  
|**adStatusOK**|1|Указывает, успешно операции, вызвавшей событие.|  
|**adStatusUnwantedEvent**|5|Предотвращает последующие уведомления до завершения выполнения метода события.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[BeginTransComplete, CommitTransComplete и RollbackTransComplete события (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[События ConnectComplete и Disconnect (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[Событие EndOfRecordset (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[Событие FetchComplete (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[Событие InfoMessage (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[События WillChangeField и FieldChangeComplete (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[Событие WillConnect (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
