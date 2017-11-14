---
title: "Событие EndOfRecordset (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4cf00efb278f6ea9937bd0fa87f929d45b8294cb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="endofrecordset-event-ado"></a>Событие EndOfRecordset (ADO)
**EndOfRecordset** событие вызывается при попытке переместить строку за пределами [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *fMoreData*  
 Объект **VARIANT_BOOL** значение, если присвоить значение VARIANT_TRUE, указывает, будут добавлены дополнительные строки **записей**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **EndOfRecordset** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие. Ему присваивается **adStatusCantDeny** Если это событие не удается запросить отмену операции, вызвавшей это событие.  
  
 Прежде чем **EndOfRecordset** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Замечания  
 **EndOfRecordset** событие может происходить, если [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) завершается с ошибкой.  
  
 Этот обработчик событий вызывается при попытке перемещения за пределами **записей** объекта, например в результате вызова **MoveNext**. Тем не менее, хотя в этом случае можно получить дополнительные записи из базы данных и добавляет их в конец **записей**. В этом случае задайте *fMoreData* значение VARIANT_TRUE и возвращают из **EndOfRecordset**. Затем вызовите **MoveNext** еще раз, чтобы получить доступ к вновь полученных записей.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)

