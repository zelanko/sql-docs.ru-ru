---
description: Свойство CommandType (ADO)
title: Свойство CommandType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: a8d92e54d88ede66f5c5f6c3c2a74bd5f0b66af0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975115"
---
# <a name="commandtype-property-ado"></a>Свойство CommandType (ADO)
Указывает тип объекта [команды](./command-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно или несколько значений [коммандтипинум](./commandtypeenum.md) .  
  
> [!NOTE]
>  Не используйте значения **Коммандтипинум** **адкмдфиле** или **адкмдтабледирект** с **CommandType**. Эти значения можно использовать только в качестве параметров с методами [Open](./open-method-ado-recordset.md) и [Requery](./requery-method.md) [набора записей](./recordset-object-ado.md).  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **CommandType** для оптимизации оценки свойства [CommandText](./commandtext-property-ado.md) .  
  
 Если для свойства **CommandType** задано значение по умолчанию **адкмдункновн**, то может возникнуть снижение производительности, так как ADO должны вызывать поставщик, чтобы определить, является ли свойство **CommandText** инструкцией SQL, хранимой процедурой или именем таблицы. Если известно, какой тип команды используется, установка свойства **CommandType** указывает ADO перейти непосредственно к соответствующему коду. Если свойство **CommandType** не соответствует типу команды в свойстве **CommandText** , то при вызове метода [EXECUTE](./execute-method-ado-command.md) возникает ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](./activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](./activeconnection-commandtext-timeout-type-size-example-jscript.md)