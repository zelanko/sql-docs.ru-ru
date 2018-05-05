---
title: Метод GetSchemaObject (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f91e7c068e5e058934e416b9c17ffd3d47a3db4d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getschemaobject-method-ado-md"></a>Метод GetSchemaObject (ADO MD)
Извлекает объект схемы ADO MD ([измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), или [член](../../../ado/reference/ado-md-api/member-object-ado-md.md)) по его [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjType*  
 Объект [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) значение, указывающее, какой тип объекта схемы (измерения, иерархии, уровня или элемента) для извлечения.  
  
 *UniqueName*  
 Объект **строка** указание **UniqueName** значение свойства объекта для извлечения.  
  
## <a name="remarks"></a>Замечания  
 **GetSchemaObject** получает объекты, используя свои уникальные имена в соответствии с **UniqueName** свойство. Имена родительских объектов не обязательно должны быть известны и родительские коллекции, не нужно заполнять для получения схемы объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
