---
description: Метод CreateParameter (ADO)
title: Метод CreateParameter (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c3ed02109806232f8301b33e8b0387ea78b6ef4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775613"
---
# <a name="createparameter-method-ado"></a>Метод CreateParameter (ADO)
Создает новый объект [Parameter](./parameter-object.md) с указанными свойствами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект **параметра** .  
  
#### <a name="parameters"></a>Параметры  
 *Имя*  
 Необязательный элемент. **Строковое** значение, содержащее имя объекта **параметра** .  
  
 *Тип*  
 Необязательный элемент. Значение [дататипинум](./datatypeenum.md) , указывающее тип данных объекта **параметра** .  
  
 *Направление*  
 Необязательный элемент. Значение [параметердиректионенум](./parameterdirectionenum.md) , указывающее тип объекта **параметра** .  
  
 *Размер*  
 Необязательный элемент. Значение **типа Long** , указывающее максимальную длину значения параметра в символах или байтах.  
  
 *Значение*  
 Необязательный элемент. **Вариант** , указывающий значение для объекта **параметра** .  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **CreateParameter** для создания нового объекта **Parameter** с указанными именем, типом, направлением, размером и значением. Любые значения, передаваемые в аргументы, записываются в соответствующие свойства **параметров** .  
  
 Этот метод не добавляет автоматически объект **Parameter** в коллекцию **Parameters** объекта [Command](./command-object-ado.md) . Это позволяет задать дополнительные свойства, значения которых будут проверяться ADO при добавлении объекта **параметра** в коллекцию.  
  
 Если в аргументе *типа* указан тип данных переменной длины, необходимо либо передать аргумент *размера* , либо задать свойство [size](./size-property-ado-parameter.md) объекта **Parameter** перед добавлением его в коллекцию **Parameters** . в противном случае возникает ошибка.  
  
 Если в аргументе *типа* указан числовой тип данных (**аднумерик** или **аддеЦимал**), необходимо также задать свойства [NumericScale](./numericscale-property-ado.md) и [Precision](./precision-property-ado.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Append и CreateParameter (Visual Basic)](./append-and-createparameter-methods-example-vb.md)   
 [Пример методов Append и CreateParameter (Visual c++)](./append-and-createparameter-methods-example-vc.md)   
 [Метод Append (ADO)](./append-method-ado.md)   
 [Объект Parameter](./parameter-object.md)   
 [Коллекция Parameters (ADO)](./parameters-collection-ado.md)