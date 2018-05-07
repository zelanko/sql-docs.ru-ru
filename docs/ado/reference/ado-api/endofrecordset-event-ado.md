---
title: Событие EndOfRecordset (ADO) | Документы Microsoft
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
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f035d61d2e8526c21960761be2db5a900666083c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
