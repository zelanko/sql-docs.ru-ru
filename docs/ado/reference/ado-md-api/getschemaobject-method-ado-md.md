---
title: Метод Жетсчемаобжект (объекты данных ActiveX (MD)) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949766"
---
# <a name="getschemaobject-method-ado-md"></a>Метод GetSchemaObject (многомерные объекты ADO)
Извлекает объект схемы объекты данных ActiveX (MD) ([измерение](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархию](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md)или [элемент](../../../ado/reference/ado-md-api/member-object-ado-md.md)) по его свойству [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjType*  
 Значение [счемаобжекттипинум](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) , указывающее тип объекта схемы (измерения, иерархии, уровня или элемента), который требуется получить.  
  
 *UniqueName*  
 **Строка** , указывающая значение свойства **UniqueName** получаемого объекта.  
  
## <a name="remarks"></a>Remarks  
 **Жетсчемаобжект** извлекает объекты, используя их уникальные имена, как указано в свойстве **UniqueName** . Имена родительских объектов не обязательно должны быть известны, а для получения объекта схемы не нужно заполнять родительские коллекции.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
