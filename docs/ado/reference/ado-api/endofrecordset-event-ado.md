---
title: Событие EndOfRecordset (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 414094da95076a7fb3781877645c5d43a03e6a7f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698218"
---
# <a name="endofrecordset-event-ado"></a>Событие EndOfRecordset (ADO)
**EndOfRecordset** событие вызывается при попытке перейти к строке после конца [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *fMoreData*  
 Объект **VARIANT_BOOL** значение, которое, если присвоить значение VARIANT_TRUE, указывающее, были добавлены дополнительные строки **записей**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **EndOfRecordset** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие. Ему будет присвоено **adStatusCantDeny** Если это событие не может запросить отмену операции, вызвавшее данное событие.  
  
 Прежде чем **EndOfRecordset** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 **EndOfRecordset** событие может происходить, если [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) сбоя операции.  
  
 Этот обработчик событий вызывается при попытке перемещения за пределами **записей** объекта, например в результате вызова **MoveNext**. Тем не менее, хотя в этом случае можно получить дополнительные записи из базы данных и добавляет их в конец **записей**. В этом случае задайте *fMoreData* значение VARIANT_TRUE, а после возврата из **EndOfRecordset**. Затем вызовите **MoveNext** еще раз, чтобы получить доступ к только что полученный записей.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
