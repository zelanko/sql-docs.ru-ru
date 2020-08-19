---
description: События WillMove и MoveComplete (ADO)
title: События Виллмове и Мовекомплете (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c992f95ae9caf96708f5fcde0c255ff8c7c6f11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441506"
---
# <a name="willmove-and-movecomplete-events-ado"></a>События WillMove и MoveComplete (ADO)
Событие **виллмове** вызывается до того, как операция ожидает изменения текущей позицией в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md). Событие **мовекомплете** вызывается после изменения текущей позицией в **наборе записей** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 Значение [евентреасоненум](../../../ado/reference/ado-api/eventreasonenum.md) , указывающее причину события. Его значением может быть **адрснмовефирст**, **адрснмовеласт**, **адрснмовенекст**, **адрснмовепревиаус**, **адрснмове**или **адрснрекуери**.  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае параметр не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове **виллмове** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **мовекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллмове** задайте для этого параметра значение **адстатусканцел** , чтобы запросить отмену ожидающей операции, или задайте для этого параметра значение **адстатусунвантедевент** , чтобы избежать появления последующих уведомлений.  
  
 Перед возвратом **мовекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллмове** или **мовекомплете** может возникать из-за следующих операций с **набором записей** : [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)и [Requery](../../../ado/reference/ado-api/requery-method.md). Эти события могут возникать из-за следующих свойств: [Filter](../../../ado/reference/ado-api/filter-property.md), [index](../../../ado/reference/ado-api/index-property.md), [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md), [примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md)и [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Эти события также возникают, если для дочернего **набора** записей подключены события **набора записей** и перемещен родительский **набор записей** .  
  
 Необходимо присвоить параметру *адстатус* значение **адстатусунвантедевент** для каждого возможного значения *адреасон* , чтобы полностью отключить уведомление о событии для любого события, включающего параметр *адреасон* .  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка по обработчику событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
