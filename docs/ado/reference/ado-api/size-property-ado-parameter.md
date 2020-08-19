---
description: Свойство Size (объект Parameter ADO)
title: Свойство Size (параметр ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
author: rothja
ms.author: jroth
ms.openlocfilehash: 78a22e22f5bf65c211a18bd68767537af164b452
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442156"
---
# <a name="size-property-ado-parameter"></a>Свойство Size (объект Parameter ADO)
Указывает максимальный размер объекта [параметра](../../../ado/reference/ado-api/parameter-object.md) в байтах или символах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , указывающее максимальный размер в байтах или символах значения в объекте **параметра** .  
  
## <a name="remarks"></a>Remarks  
 Свойство **size** используется для определения максимального размера значений, записываемых или считываемых из свойства [value](../../../ado/reference/ado-api/value-property-ado.md) объекта **Parameter** .  
  
 Если для объекта **параметра** задан тип данных переменной длины (например, любой **строковый** тип, например **адварчар**), необходимо задать свойство **size** объекта перед его добавлением в коллекцию [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) . в противном случае возникает ошибка.  
  
 Если объект **параметра** уже добавлен в коллекцию **Parameters** объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) и вы измените его тип на тип данных переменной длины, необходимо задать свойство **size** объекта **Parameter** перед выполнением объекта **команды** . в противном случае возникает ошибка.  
  
 Если вы используете метод [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) для получения сведений о параметрах от поставщика и возвращает один или несколько объектов **параметров** типа данных переменной длины, ADO может выделить память для параметров на основе максимального возможного размера, что может вызвать ошибку во время выполнения. Чтобы предотвратить возникновение ошибки, необходимо явно задать свойство **size** для этих параметров перед выполнением команды.  
  
 Свойство **size** доступно для чтения и записи.  
  
## <a name="applies-to"></a>Применение  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Свойство Size (объект Stream ADO)](../../../ado/reference/ado-api/size-property-ado-stream.md)
