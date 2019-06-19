---
title: LockTypeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9dbc6e9e78fc08be2bba08d0fbeb897496a2058b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694934"
---
# <a name="locktypeenum"></a>LockTypeEnum
Указывает тип блокировки, уделено записей во время редактирования.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Указывает оптимистичный пакетные обновления. Требуется для пакетного режима обновления.|  
|**adLockOptimistic**|3|Указывает, оптимистической блокировки, записей. Поставщик использует оптимистической блокировки, Блокировка записей только в том случае, когда вы вызываете [обновления](../../../ado/reference/ado-api/update-method.md) метод.|  
|**adLockPessimistic**|2|Указывает, пессимистической блокировки записей. Поставщик не, что необходима для обеспечения успешного редактирования записей, обычно путем блокировки записей в источнике данных сразу же после изменения.|  
|**adLockReadOnly**|1|Указывает только для чтения записи. Невозможно изменить данные.|  
|**adLockUnspecified**|-1|Не указан тип блокировки. Для клонов клон создается с тем же типом блокировки, что и исходный.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
