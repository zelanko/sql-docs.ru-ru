---
title: Метод CreateParameter (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 865b2b0b8009b03e33e24f72ab4f336910a17ace
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277253"
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
 *Название*  
 Необязательный параметр. Объект **строка** значение, содержащее имя **параметр** объекта.  
  
 *Тип*  
 Необязательный параметр. Объект [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значение, указывающее тип данных **параметр** объекта.  
  
 *Направление*  
 Необязательный параметр. Объект [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) значение, указывающее тип **параметр** объекта.  
  
 *Размер*  
 Необязательный параметр. Объект **длинные** значение, которое указывает максимальную длину для значения параметра в символах или байтах.  
  
 *Value*  
 Необязательный параметр. Объект **Variant** , определяет значение для **параметр** объекта.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CreateParameter** метод для создания нового **параметр** объект с указанным именем, тип, направление, размер и значение. Все значения, переданные аргументы записываются в соответствующий **параметр** свойства.  
  
 Этот метод не добавляет автоматически **параметр** объект **параметры** коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Это позволяет задать дополнительные свойства которого ADO значения будет проверена при присоединении **параметр** в коллекцию.  
  
 Если указать тип данных переменной длины в *тип* аргумент, необходимо либо передать *размер* аргумент или набор [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) свойство **параметр**  объекта перед его добавлением **параметры** коллекции; в противном случае возникает ошибка.  
  
 При указании типа numeric (**adNumeric** или **adDecimal**) в *тип* аргумента, то необходимо также задать [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) и [Точности](../../../ado/reference/ado-api/precision-property-ado.md) свойства.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Добавление и пример CreateParameter методы (Visual Basic)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Добавление и пример методы CreateParameter (VC ++)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append-метод (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Объект параметра](../../../ado/reference/ado-api/parameter-object.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
