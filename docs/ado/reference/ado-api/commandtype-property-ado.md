---
description: Свойство CommandType (ADO)
title: Свойство CommandType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: rothja
ms.author: jroth
ms.openlocfilehash: 435e2c0562abcccbb6ec6e139491af280e976cfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450816"
---
# <a name="commandtype-property-ado"></a>Свойство CommandType (ADO)
Указывает тип объекта [команды](../../../ado/reference/ado-api/command-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно или несколько значений [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) .  
  
> [!NOTE]
>  Не используйте значения **Коммандтипинум** **адкмдфиле** или **адкмдтабледирект** с **CommandType**. Эти значения можно использовать только в качестве параметров с методами [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Комментарии  
 Используйте свойство **CommandType** для оптимизации оценки свойства [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) .  
  
 Если для свойства **CommandType** задано значение по умолчанию **адкмдункновн**, то может возникнуть снижение производительности, так как ADO должны вызывать поставщик, чтобы определить, является ли свойство **CommandText** инструкцией SQL, хранимой процедурой или именем таблицы. Если известно, какой тип команды используется, установка свойства **CommandType** указывает ADO перейти непосредственно к соответствующему коду. Если свойство **CommandType** не соответствует типу команды в свойстве **CommandText** , то при вызове метода [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) возникает ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
