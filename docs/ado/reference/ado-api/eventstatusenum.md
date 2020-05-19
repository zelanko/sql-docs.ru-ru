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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1abce457e64c7f6865f94b85473fbc589e5ffb4f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755151"
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
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[События Бегинтранскомплете, Коммиттранскомплете и Роллбакктранскомплете (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[События ConnectComplete и Disconnect (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[Событие EndOfRecordset (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[Событие ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[Событие FetchComplete (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[Событие InfoMessage (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[События WillChangeField и FieldChangeComplete (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[Событие WillConnect (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
