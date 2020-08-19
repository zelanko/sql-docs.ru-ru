---
description: EventStatusEnum
title: Евентстатусенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d696d7b971b5f6624a85addb3f023f2090ac90d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443906"
---
# <a name="eventstatusenum"></a>EventStatusEnum
Указывает текущее состояние выполнения события.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адстатусканцел**|4|Запрашивает отмену операции, которая привела к возникновению события.|  
|**адстатускантдени**|3|Указывает, что операция не может запросить отмену ожидающей операции.|  
|**adStatusErrorsOccurred**|2|Указывает, что операция, вызвавшая событие, завершилась сбоем из-за ошибки или ошибок.|  
|**adStatusOK**|1|Указывает, что операция, вызвавшая событие, прошла успешно.|  
|**адстатусунвантедевент**|5|Предотвращает последующие уведомления до завершения выполнения метода события.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Евентстатус. CANCEL|  
|Адоенумс. Евентстатус. КАНТДЕНИ|  
|Адоенумс. Евентстатус. ЕРРОРСОККУРРЕД|  
|Адоенумс. Евентстатус. ОК|  
|Адоенумс. Евентстатус. УНВАНТЕДЕВЕНТ|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [События Бегинтранскомплете, Коммиттранскомплете и Роллбакктранскомплете (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)  

        [События ConnectComplete и Disconnect (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)  

        [Событие EndOfRecordset (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)  

        [Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)  
    :::column-end:::
    :::column:::
        [Событие FetchComplete (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)  

        [Событие InfoMessage (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)  

        [События WillChangeField и FieldChangeComplete (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)  

        [События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)  
    :::column-end:::
    :::column:::
        [События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)  

        [Событие WillConnect (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)  

        [Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)  

        [События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)  
    :::column-end:::
:::row-end:::
