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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: af796c36bd2960730536ec07ac49614876311e84
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933291"
---
# <a name="createparameter-method-ado"></a>Метод CreateParameter (ADO)
Создает новый [параметр](../../../ado/reference/ado-api/parameter-object.md) объект с указанными свойствами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **параметр** объекта.  
  
#### <a name="parameters"></a>Параметры  
 *Name*  
 Необязательный параметр. Объект **строка** значение, содержащее имя **параметр** объекта.  
  
 *Тип*  
 Необязательный параметр. Объект [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значение, указывающее тип данных **параметр** объекта.  
  
 *Направление*  
 Необязательный параметр. Объект [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) значение, указывающее тип **параметр** объекта.  
  
 *Размер*  
 Необязательный параметр. Объект **Long** значение, которое указывает максимальную длину для значения параметра в символах или байтах.  
  
 *Значение*  
 Необязательный параметр. Объект **Variant** , указывающее значение для **параметр** объекта.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CreateParameter** метод для создания нового **параметр** объект с указанным именем, типом, направление, размер и значением. Все значения, указываемые в аргументах записываются в соответствующий **параметр** свойства.  
  
 Этот метод не добавляет автоматически **параметр** объект **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Это позволяет задать дополнительные свойства, которого ADO значения будет проверять при присоединении **параметр** в коллекцию.  
  
 Если указан тип данных переменной длины в *тип* аргумент, необходимо либо передать *размер* аргумент или набора [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) свойство **параметр**  объекта перед его добавлением **параметры** коллекции; в противном случае возникает ошибка.  
  
 При указании типа numeric (**adNumeric** или **adDecimal**) в *тип* аргумента, то необходимо также задать [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) и [Точности](../../../ado/reference/ado-api/precision-property-ado.md) свойства.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Append и CreateParameter методы (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Append и CreateParameter методы (Visual C++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Метод append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Объект параметра](../../../ado/reference/ado-api/parameter-object.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
