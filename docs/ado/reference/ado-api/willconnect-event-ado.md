---
title: Событие WillConnect (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fc1ac74e7e3d521bae587957f5f95771e5a5268
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945851"
---
# <a name="willconnect-event-ado"></a>Событие WillConnect (ADO)
**WillConnect** событие вызывается до начала соединения.  
  
 **Область применения:** [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *connectionString*  
 Объект **строка** , содержащий сведения о соединении для ожидающего подключения.  
  
 *UserID*  
 Объект **строка** , содержащий имя пользователя для ожидающего подключения.  
  
 *Пароль*  
 Объект **строка** , содержащий пароль для ожидающего подключения.  
  
 *Параметры*  
 Объект **Long** значение, указывающее, каким образом следует оценить, поставщик *ConnectionString*. Единственным вариантом является **adAsyncOpen**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда это событие вызывается, этот параметр имеет значение **adStatusOK** по умолчанию. Ему будет присвоено **adStatusCantDeny** Если событие не может запросить отмену отложенной операции.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления. Присвойте этому параметру значение **adStatusCancel** для запроса операции соединения, которая вызвала отмены этого уведомления.  
  
 *pConnection*  
 [Подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, для которого применяется это уведомление о событии. Изменения в параметры **подключения** по **WillConnect** обработчик событий не окажет никакого воздействия **подключения**.  
  
## <a name="remarks"></a>Примечания  
 Когда **WillConnect** вызове *ConnectionString*, *UserID*, *пароль*, и *параметры* присвоено установить операцией, вызвавшее данное событие (ожидающего подключения), который может быть изменен перед событием возвращает значения. **WillConnect** может возвратить запрос отмены ожидающего подключения.  
  
 Когда это событие отменяется, **ConnectComplete** будет вызываться с его *adStatus* параметру присвоить **adStatusErrorsOccurred**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
