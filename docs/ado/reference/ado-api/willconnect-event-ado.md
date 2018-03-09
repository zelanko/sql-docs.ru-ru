---
title: "Событие WillConnect (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f80b08a53784a215d58d7f36697207f4d8c3c942
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="willconnect-event-ado"></a>Событие WillConnect (ADO)
**WillConnect** событие вызывается до начала соединения.  
  
 **Область применения:** [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 Объект **строка** , содержащий сведения о соединении для ожидания соединения.  
  
 *UserID*  
 Объект **строка** , содержащий имя пользователя для ожидания соединения.  
  
 *Пароль*  
 Объект **строка** , содержащее пароль для ожидания соединения.  
  
 *Параметры*  
 Объект **длинные** значение, указывающее, как следует оценивать поставщик *ConnectionString*. Единственным вариантом является **adAsyncOpen**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда это событие вызывается, этот параметр имеет значение **adStatusOK** по умолчанию. Ему присваивается **adStatusCantDeny** Если событие нельзя запросить отмену отложенной операции.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений. Присвойте этому параметру значение **adStatusCancel** для запроса операции соединения, которая вызвала отмены этого уведомления.  
  
 *pConnection*  
 [Подключения](../../../ado/reference/ado-api/connection-object-ado.md) объектов, для которого применяется это уведомление о событии. Изменения параметров **подключения** по **WillConnect** обработчик событий не повлияет **соединения**.  
  
## <a name="remarks"></a>Remarks  
 Когда **WillConnect** вызове *ConnectionString*, *UserID*, *пароль*, и *параметры* параметры устанавливаются значения, заданные в операции, вызвавшего это событие (Ожидание подключения) и может быть изменено до завершения события. **WillConnect** может вернуть запрос отмены ожидающих соединений.  
  
 При отмене этого события **ConnectComplete** будет вызываться с его *adStatus* равным **adStatusErrorsOccurred**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
