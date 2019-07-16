---
title: Метод GetSchemaObject (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 690c81a46c62c8844780e82b5c82a0ff7301105d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949766"
---
# <a name="getschemaobject-method-ado-md"></a>Метод GetSchemaObject (многомерные объекты ADO)
Извлекает объект схемы ADO MD ([измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), или [член](../../../ado/reference/ado-md-api/member-object-ado-md.md)) по его [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjType*  
 Объект [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) значение, указывающее тип объекта схемы (измерения, иерархии, уровня или элемента) для извлечения.  
  
 *UniqueName*  
 Объект **строка** указание **UniqueName** значение свойства объекта для извлечения.  
  
## <a name="remarks"></a>Примечания  
 **GetSchemaObject** извлекает объекты, используя свои уникальные имена, указанный в **UniqueName** свойство. Имена родительских объектов не обязательно должны быть известны и родительские коллекции не обязательно должны быть заполнено, чтобы получить объект схемы.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
