---
description: FieldEnum
title: Фиелденум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2bdcec83c211f71803ea64b7b78f3e6f8c76dee6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973135"
---
# <a name="fieldenum"></a>FieldEnum
Задает специальные поля, на которые ссылается коллекция [Fields](./fields-collection-ado.md) объекта [Record](./record-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Эти константы предоставляют "ярлык" для доступа к специальным полям, связанным с **записью**. Получите объект [поля](./field-object.md) из коллекции **полей** , а затем получите его содержимое со свойством [value](./value-property-ado.md) объекта **field** .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**аддефаултстреам**|-1|Ссылается на поле, содержащее объект [потока](./stream-object-ado.md) по умолчанию, связанный с **записью**.|  
|**adRecordURL**|-2|Ссылается на поле, содержащее абсолютную строку URL-адреса для текущей **записи**.|