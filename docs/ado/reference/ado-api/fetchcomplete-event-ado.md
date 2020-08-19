---
description: Событие FetchComplete (ADO)
title: Событие Фетчкомплете (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
author: rothja
ms.author: jroth
ms.openlocfilehash: a4fd58f7783b8fdf2b98d8e295bbf96137cfa5ff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443826"
---
# <a name="fetchcomplete-event-ado"></a>Событие FetchComplete (ADO)
Событие **фетчкомплете** вызывается после того, как все записи в длинной асинхронной операции были извлечены в [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение **адстатус** равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) . При вызове этого события этот параметр устанавливается в значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** , если операция завершилась ошибкой.  
  
 Перед возвратом этого события задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . Объект, для которого были получены записи.  
  
## <a name="remarks"></a>Remarks  
 Чтобы использовать **фетчкомплете** с Microsoft Visual Basic, требуется Visual Basic 6,0 или более поздней версии.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
