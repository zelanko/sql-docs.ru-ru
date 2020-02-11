---
title: Евентреасоненум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c37a7385cc3aabb725f86261203d22b5b10c3be6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918876"
---
# <a name="eventreasonenum"></a>EventReasonEnum
Указывает причину возникновения события.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адрснадднев**|1|Операция добавила новую запись.|  
|**адрснклосе**|9|**Набор записей**закрыт операцией.|  
|**адрснделете**|2|Операция удалила запись.|  
|**адрснфирстчанже**|11|Операция выполнила первое изменение в записи.|  
|**адрснмове**|10|Операция переместила указатель записи в **наборе записей**.|  
|**адрснмовефирст**|12|Операция переместила указатель записи на первую запись в **наборе записей**.|  
|**адрснмовеласт**|15|Операция переместила указатель записи на последнюю запись в **наборе записей**.|  
|**адрснмовенекст**|13|Операция переместила указатель записи на следующую запись в **наборе записей**.|  
|**адрснмовепревиаус**|14|Операция переместила указатель записи на предыдущую запись в **наборе записей**.|  
|**адрснрекуери**|7|Операция запросила [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**адрснресинч**|8|Операция повторно синхронизирует **набор записей** с базой данных.|  
|**адрснундоадднев**|5|Операция обращается к добавлению новой записи.|  
|**адрснундоделете**|6|Операция обращается к удалению записи.|  
|**адрснундаупдате**|4|Операция обращается к обновлению записи.|  
|**адрснупдате**|3|Операция обновила существующую запись.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Евентреасон. ADDNEW|  
|Адоенумс. Евентреасон. CLOSE|  
|Адоенумс. Евентреасон. DELETE|  
|Адоенумс. Евентреасон. ФИРСТЧАНЖЕ|  
|Адоенумс. Евентреасон. MOVE|  
|Адоенумс. Евентреасон. MOVEFIRST|  
|Адоенумс. Евентреасон. MOVELAST|  
|Адоенумс. Евентреасон. MOVENEXT|  
|Адоенумс. Евентреасон. MOVEPREVIOUS|  
|Адоенумс. Евентреасон. Requery|  
|Адоенумс. Евентреасон. resynch|  
|Адоенумс. Евентреасон. УНДОАДДНЕВ|  
|Адоенумс. Евентреасон. УНДОДЕЛЕТЕ|  
|Адоенумс. Евентреасон. УНДАУПДАТЕ|  
|Адоенумс. Евентреасон. UPDATE|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[События WillChangeRecord и RecordChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[События WillChangeRecordset и RecordsetChangeComplete (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[События WillMove и MoveComplete (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
