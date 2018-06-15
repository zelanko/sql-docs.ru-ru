---
title: ConnectComplete и отключения событий (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ac6301a8ed8ab0c84f26225e20c2bfd971ff761
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276843"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete и отключения событий (ADO)
**ConnectComplete** событие вызывается после начала подключения. **Disconnect** событие вызывается после завершения соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) возвращает значение, всегда **adStatusOK**.  
  
 При **ConnectComplete** — вызывается, этот параметр имеет значение **adStatusCancel** Если **WillConnect** событий запросил отмену ожидающего подключения.  
  
 Перед возвратом любого события, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений. Тем не менее, закрытие и повторное открытие [подключения](../../../ado/reference/ado-api/connection-object-ado.md) вызывает повторного возникновения этих событий.  
  
 *pConnection*  
 **Подключения** объектов, для которого применяется это событие.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
