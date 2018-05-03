---
title: FieldEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6caaf8db2b8f2e19060f6e9766bb3650ac9b5400
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fieldenum"></a>FieldEnum
Указывает специальные поля, на которые ссылается [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
## <a name="remarks"></a>Замечания  
 Эти константы предоставляют «ярлык» для доступа к специальные поля, связанные с **записи**. Получить [поле](../../../ado/reference/ado-api/field-object.md) объекта из **поля** коллекции и получение его содержимое **поле** объекта [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Ссылается на поле, содержащее значение по умолчанию [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта, связанного с **записи**.|  
|**adRecordURL**|-2|Ссылается на поле, содержащее абсолютный URL-адрес строки для текущего **записи**.|
