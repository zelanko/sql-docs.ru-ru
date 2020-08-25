---
description: FieldEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: cad540a13fbad480f795049df0d0150188df4283
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775453"
---
# <a name="fieldenum"></a>FieldEnum
Задает специальные поля, на которые ссылается коллекция [Fields](./fields-collection-ado.md) объекта [Record](./record-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Эти константы предоставляют "ярлык" для доступа к специальным полям, связанным с **записью**. Получите объект [поля](./field-object.md) из коллекции **полей** , а затем получите его содержимое со свойством [value](./value-property-ado.md) объекта **field** .  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**аддефаултстреам**|-1|Ссылается на поле, содержащее объект [потока](./stream-object-ado.md) по умолчанию, связанный с **записью**.|  
|**adRecordURL**|-2|Ссылается на поле, содержащее абсолютную строку URL-адреса для текущей **записи**.|