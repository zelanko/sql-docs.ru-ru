---
title: События WillMove и Movecomplete (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c91f3166b493ac1e2fada3e759cb107e34c7ca81
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945911"
---
# <a name="willmove-and-movecomplete-events-ado"></a>События WillMove и MoveComplete (ADO)
**События WillMove** событие вызывается перед отложенная операция изменяет текущую позицию в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **MoveComplete** событие вызывается после текущей позиции в **записей** изменения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину для данного события. Его значение может быть **adRsnMoveFirst**, **adRsnMoveLast**, **adRsnMoveNext**, **adRsnMovePrevious**, **adRsnMove** , или **adRsnRequery**.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае не задан параметр.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **события WillMove** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие. Ему будет присвоено **adStatusCantDeny** Если это событие не может запросить отмену отложенной операции.  
  
 Когда **MoveComplete** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или для **adStatusErrorsOccurred** Если не удалось выполнить операцию.  
  
 Прежде чем **события WillMove** возвращает, присвойте этому параметру значение **adStatusCancel** запросить отмену отложенной операции или присвойте этому параметру значение **adStatusUnwantedEvent** Чтобы предотвратить последующие уведомления.  
  
 Прежде чем **MoveComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pRecordset*  
 Объект [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 Объект **события WillMove** или **MoveComplete** событие может происходить из-за следующих **записей** операций: [Откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md), [переместить](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), и [Requery](../../../ado/reference/ado-api/requery-method.md). Эти события могут происходить из-за следующие свойства: [Фильтр](../../../ado/reference/ado-api/filter-property.md), [индекс](../../../ado/reference/ado-api/index-property.md), [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md), [примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md), и [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Эти события также возникать, если дочерний элемент **записей** имеет **набор записей** события подключения и родительским **записей** перемещается.  
  
 Необходимо задать *adStatus* параметр **adStatusUnwantedEvent** для каждого возможного *adReason* значение, чтобы полностью остановить уведомления о событии для любых событий, включает в себя *adReason* параметра.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
