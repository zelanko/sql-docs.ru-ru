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
ms.openlocfilehash: 9dbc74fbca54ab1bdafb3c0f2ba941aee49f2213
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776853"
---
# <a name="willmove-and-movecomplete-events-ado"></a>События WillMove и MoveComplete (ADO)
Событие **виллмове** вызывается до того, как операция ожидает изменения текущей позицией в [наборе записей](./recordset-object-ado.md). Событие **мовекомплете** вызывается после изменения текущей позицией в **наборе записей** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 Значение [евентреасоненум](./eventreasonenum.md) , указывающее причину события. Его значением может быть **адрснмовефирст**, **адрснмовеласт**, **адрснмовенекст**, **адрснмовепревиаус**, **адрснмове**или **адрснрекуери**.  
  
 *pError*  
 Объект [ошибки](./error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае параметр не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) .  
  
 При вызове **виллмове** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **мовекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллмове** задайте для этого параметра значение **адстатусканцел** , чтобы запросить отмену ожидающей операции, или задайте для этого параметра значение **адстатусунвантедевент** , чтобы избежать появления последующих уведомлений.  
  
 Перед возвратом **мовекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект [Recordset](./recordset-object-ado.md) . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллмове** или **мовекомплете** может возникать из-за следующих операций с **набором записей** : [Open](./open-method-ado-recordset.md), [Move](./move-method-ado.md), [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](./addnew-method-ado.md)и [Requery](./requery-method.md). Эти события могут возникать из-за следующих свойств: [Filter](./filter-property.md), [index](./index-property.md), [Bookmark](./bookmark-property-ado.md), [примеры absolutepage](./absolutepage-property-ado.md)и [примеры AbsolutePosition](./absoluteposition-property-ado.md). Эти события также возникают, если для дочернего **набора** записей подключены события **набора записей** и перемещен родительский **набор записей** .  
  
 Необходимо присвоить параметру *адстатус* значение **адстатусунвантедевент** для каждого возможного значения *адреасон* , чтобы полностью отключить уведомление о событии для любого события, включающего параметр *адреасон* .  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Сводка по обработчику событий ADO](../../guide/data/ado-event-handler-summary.md)   
 [Объект Recordset (ADO)](./recordset-object-ado.md)