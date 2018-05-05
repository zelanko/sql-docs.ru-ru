---
title: Событие FetchComplete (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59c3adb6b0ad683b40dac2cf4547800bf7398067
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fetchcomplete-event-ado"></a>Событие FetchComplete (ADO)
**FetchComplete** событие вызывается после получения всех записей в длительных асинхронных операций в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение **adStatus** — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. Когда это событие вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие или для **adStatusErrorsOccurred** при сбое операции.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pRecordset*  
 Объект **записей** объекта. Объект, для которого были получены записей.  
  
## <a name="remarks"></a>Замечания  
 Для использования **FetchComplete** с помощью Microsoft Visual Basic, Visual Basic 6.0 или более поздней версии не требуется.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
