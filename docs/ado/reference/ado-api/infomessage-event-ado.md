---
title: Событие InfoMessage (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 516e6a95ba98f1b8d66ddf9f417460ef2a6b7dc0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028031"
---
# <a name="infomessage-event-ado"></a>Событие InfoMessage (ADO)
**InfoMessage** событие вызывается при возникновении предупреждения во время **ConnectionEvent** операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Этот параметр содержит все ошибки, которые возвращаются. Если возвращается несколько ошибок, перечислить **ошибки** коллекции для их поиска.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. При возникновении предупреждения, *adStatus* присваивается **adStatusOK** и *pError* , появится предупреждение.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pConnection*  
 Объект [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Соединение, для которого возникло предупреждение. Например, предупреждения могут возникнуть при открытии **подключения** объекта или выполнении [команда](../../../ado/reference/ado-api/command-object-ado.md) на **подключения**.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
