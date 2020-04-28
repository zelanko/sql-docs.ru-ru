---
title: Фиелденум | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932685"
---
# <a name="fieldenum"></a>FieldEnum
Задает специальные поля, на которые ссылается коллекция [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) объекта [Record](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Эти константы предоставляют "ярлык" для доступа к специальным полям, связанным с **записью**. Получите объект [поля](../../../ado/reference/ado-api/field-object.md) из коллекции **полей** , а затем получите его содержимое со свойством [value](../../../ado/reference/ado-api/value-property-ado.md) объекта **field** .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**аддефаултстреам**|-1|Ссылается на поле, содержащее объект [потока](../../../ado/reference/ado-api/stream-object-ado.md) по умолчанию, связанный с **записью**.|  
|**adRecordURL**|-2|Ссылается на поле, содержащее абсолютную строку URL-адреса для текущей **записи**.|
