---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8883679a85d1e134b1759c90cde524bb97995130
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932869"
---
# <a name="eventstatusenum"></a>EventStatusEnum
Указывает текущее состояние выполнения события.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адстатусканцел**|4|Запрашивает отмену операции, которая привела к возникновению события.|  
|**адстатускантдени**|3|Указывает, что операция не может запросить отмену ожидающей операции.|  
|**адстатусеррорсоккурред**|2|Указывает, что операция, вызвавшая событие, завершилась сбоем из-за ошибки или ошибок.|  
|**адстатусок**|1|Указывает, что операция, вызвавшая событие, прошла успешно.|  
|**адстатусунвантедевент**|5|Предотвращает последующие уведомления до завершения выполнения метода события.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Евентстатус. CANCEL|  
|Адоенумс. Евентстатус. КАНТДЕНИ|  
|Адоенумс. Евентстатус. ЕРРОРСОККУРРЕД|  
|Адоенумс. Евентстатус. ОК|  
|Адоенумс. Евентстатус. УНВАНТЕДЕВЕНТ|  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[События Бегинтранскомплете, Коммиттранскомплете и Роллбакктранскомплете (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[События ConnectComplete и Disconnect (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[Событие EndOfRecordset (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[Событие FetchComplete (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[Событие InfoMessage (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[События WillChangeField и FieldChangeComplete (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[Событие WillConnect (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
