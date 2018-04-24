---
title: События InfoMessage (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 154e752495745eb24018275f87109986ebf168bb
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="infomessage-event-ado"></a>События InfoMessage (ADO)
**InfoMessage** событие вызывается каждый раз при возникновении предупреждения во время **ConnectionEvent** операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Этот параметр содержит все ошибки, возвращаются. Если возвращается несколько ошибок, перечислить **ошибки** коллекции для их поиска.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. При возникновении предупреждения, *adStatus* равно **adStatusOK** и *pError* , появится предупреждение.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pConnection*  
 Объект [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Соединение, для которого возникло предупреждение. Например, предупреждения могут возникнуть при открытии **подключения** объекта или выполнении [команда](../../../ado/reference/ado-api/command-object-ado.md) на **соединения**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
