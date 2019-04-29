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
manager: craigg
ms.openlocfilehash: fe681a0f93dd88ad7f4752daf213817c21b054ad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043768"
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
