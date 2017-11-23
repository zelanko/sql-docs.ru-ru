---
title: "EventReasonEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: EventReasonEnum
helpviewer_keywords: EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f16c5e9ba0c79a8920c4a7d4c9bcd9171d23ec1e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="eventreasonenum"></a>EventReasonEnum
Указывает причину, вызвавшего событие.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|Операция добавления новой записи.|  
|**adRsnClose**|9|Операция закрытия **записей**.|  
|**adRsnDelete**|2|Удалить операцию записи.|  
|**adRsnFirstChange**|11|Операция выполнена первое изменение с записью.|  
|**adRsnMove**|10|Операция перемещен указатель записи в **записей**.|  
|**adRsnMoveFirst**|12|Операция перемещен указатель записи первой записи в **записей**.|  
|**adRsnMoveLast**|15|Операция перемещен указатель записи в последней записи в **записей**.|  
|**adRsnMoveNext**|13|Операция перемещен указатель записи следующей записи в **записей**.|  
|**adRsnMovePrevious**|14|Операция перемещен указатель записи к предыдущей записи в **записей**.|  
|**adRsnRequery**|7|Операция опросить [записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adRsnResynch**|8|Операция повторной синхронизации **записей** с базой данных.|  
|**adRsnUndoAddNew**|5|Операция добавления новой записи в обратном направлении.|  
|**adRsnUndoDelete**|6|Операция удаления записи в обратном направлении.|  
|**adRsnUndoUpdate**|4|Операция обновления записи в обратном направлении.|  
|**adRsnUpdate**|3|Операция обновления существующей записи.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
