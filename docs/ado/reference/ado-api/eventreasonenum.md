---
title: EventReasonEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b9645e05ce3387ea5948cca07b91ecdc80cd4b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="eventreasonenum"></a>EventReasonEnum
Указывает причину, вызвавшего событие.  
  
|Константа|Значение|Описание|  
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
