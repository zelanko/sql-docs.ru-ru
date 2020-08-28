---
description: Событие EndOfRecordset (ADO)
title: Событие Ендофрекордсет (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c0bd91666040a87d104ff4a9c0036596b711a51
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973801"
---
# <a name="endofrecordset-event-ado"></a>Событие EndOfRecordset (ADO)
Событие **ендофрекордсет** вызывается при попытке переместиться в строку после конца [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *фморедата*  
 **VARIANT_BOOL** значение, которое при установке значения VARIANT_TRUE указывает, что в **набор записей**были добавлены дополнительные строки.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове **ендофрекордсет** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену операции, вызвавшей это событие.  
  
 Перед возвратом **ендофрекордсет** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 При сбое операции [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) может возникнуть событие **ендофрекордсет** .  
  
 Этот обработчик событий вызывается при попытке переместиться за пределы объекта **набора записей** , возможно, в результате вызова **MoveNext**. Однако в этом событии можно получить дополнительные записи из базы данных и добавить их в конец **набора записей**. В этом случае задайте для *фморедата* значение VARIANT_TRUE и вернитесь из **ендофрекордсет**. Затем снова вызовите **MoveNext** для доступа к вновь полученным записям.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
