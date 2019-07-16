---
title: FieldEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fe89d90510e95468e18b0d744ff566f69654320
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932685"
---
# <a name="fieldenum"></a>FieldEnum
Указывает специальные поля, на которые ссылается [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
## <a name="remarks"></a>Примечания  
 Эти константы предоставляют «ярлык» специальные поля, связанные с доступом к **записи**. Получить [поле](../../../ado/reference/ado-api/field-object.md) объекта из **поля** коллекции, а затем получать его содержимое с **поле** объекта [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Ссылается на поле, содержащее значение по умолчанию [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объект, связанный с **записи**.|  
|**adRecordURL**|-2|Ссылается на поле, содержащее абсолютный URL-адрес строки для текущего **записи**.|
