---
title: "WillMove и MoveComplete события (ADO) | Документы Microsoft"
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
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac06472367c1ebb000d317a6373ea911241e45f8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove и MoveComplete события (ADO)
**WillMove** событие вызывается перед ожидающая выполнения операция изменяет текущую позицию в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **MoveComplete** событие вызывается после текущей позиции в **записей** изменения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину возникновения данного события. Его значение может быть **adRsnMoveFirst**, **adRsnMoveLast**, **adRsnMoveNext**, **adRsnMovePrevious**, **adRsnMove** , или **adRsnRequery**.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае значение параметра не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **WillMove** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие. Ему присваивается **adStatusCantDeny** Если это событие не удается запросить отмену отложенной операции.  
  
 Когда **MoveComplete** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие или для **adStatusErrorsOccurred** Если не удалось выполнить операцию.  
  
 Прежде чем **WillMove** возвращает, присвойте этому параметру значение **adStatusCancel** запрашивать отмену отложенной операции или установите этот параметр, **adStatusUnwantedEvent** Чтобы предотвратить последующие уведомления.  
  
 Прежде чем **MoveComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pRecordset*  
 Объект [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Remarks  
 Объект **WillMove** или **MoveComplete** событие может происходить из-за следующих **записей** операции: [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md), [переместить](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), и [Requery](../../../ado/reference/ado-api/requery-method.md). Эти события могут происходить из-за следующих свойств: [фильтра](../../../ado/reference/ado-api/filter-property.md), [индекс](../../../ado/reference/ado-api/index-property.md), [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)и [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Эти события также возникнуть, если дочерний элемент **записей** имеет **записей** события подключен и родительским **набора записей** перемещается.  
  
 Необходимо задать *adStatus* параметр **adStatusUnwantedEvent** для каждого возможного *adReason* значение для полной остановки уведомление о событии для любых событий, включает в себя *adReason* параметра.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
