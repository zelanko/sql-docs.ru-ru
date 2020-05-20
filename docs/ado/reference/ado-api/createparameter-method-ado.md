---
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
ms.openlocfilehash: 6cd78e3cbe992a3f2df5046a26eca990479cb3fd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760220"
---
# <a name="createparameter-method-ado"></a>Метод CreateParameter (ADO)
Создает новый объект [Parameter](../../../ado/reference/ado-api/parameter-object.md) с указанными свойствами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект **параметра** .  
  
#### <a name="parameters"></a>Параметры  
 *Name*  
 Необязательный элемент. **Строковое** значение, содержащее имя объекта **параметра** .  
  
 *Type*  
 Необязательный элемент. Значение [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) , указывающее тип данных объекта **параметра** .  
  
 *Направление*  
 Необязательный элемент. Значение [параметердиректионенум](../../../ado/reference/ado-api/parameterdirectionenum.md) , указывающее тип объекта **параметра** .  
  
 *Размер*  
 Необязательный элемент. Значение **типа Long** , указывающее максимальную длину значения параметра в символах или байтах.  
  
 *Значение*  
 Необязательный элемент. **Вариант** , указывающий значение для объекта **параметра** .  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **CreateParameter** для создания нового объекта **Parameter** с указанными именем, типом, направлением, размером и значением. Любые значения, передаваемые в аргументы, записываются в соответствующие свойства **параметров** .  
  
 Этот метод не добавляет автоматически объект **Parameter** в коллекцию **Parameters** объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) . Это позволяет задать дополнительные свойства, значения которых будут проверяться ADO при добавлении объекта **параметра** в коллекцию.  
  
 Если в аргументе *типа* указан тип данных переменной длины, необходимо либо передать аргумент *размера* , либо задать свойство [size](../../../ado/reference/ado-api/size-property-ado-parameter.md) объекта **Parameter** перед добавлением его в коллекцию **Parameters** . в противном случае возникает ошибка.  
  
 Если в аргументе *типа* указан числовой тип данных (**аднумерик** или **аддеЦимал**), необходимо также задать свойства [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) и [Precision](../../../ado/reference/ado-api/precision-property-ado.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Append и CreateParameter (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Пример методов Append и CreateParameter (Visual c++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
