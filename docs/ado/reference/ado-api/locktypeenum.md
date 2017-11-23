---
title: "LockTypeEnum | Документы Microsoft"
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
f1_keywords: LockTypeEnum
helpviewer_keywords: LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 528d26feb0037a3717ff7b1a9b05606e3ecf37c9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="locktypeenum"></a>LockTypeEnum
Указывает тип блокировка, установленная на записи во время редактирования.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Указывает оптимистичный пакетных обновлений. Требуется для пакетного режима обновления.|  
|**adLockOptimistic**|3|Указывает, оптимистической блокировки, по одной записи. Поставщик использует оптимистической блокировки блокировки записи только при вызове [обновление](../../../ado/reference/ado-api/update-method.md) метод.|  
|**adLockPessimistic**|2|Указывает пессимистичных блокировок, по одной записи. Поставщик не то, что является обязательным для обеспечения успешного редактирования записей, обычно блокирование записей в источнике данных сразу же после изменения.|  
|**adLockReadOnly**|1|Указывает записи только для чтения. Невозможно изменить данные.|  
|**adLockUnspecified**|-1|Не указывает тип блокировки. Клонов копия создается с тем же типом блокировки, что и исходный.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Clone (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Событие WillExecute (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
