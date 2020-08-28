---
description: Метод GetSchemaObject (многомерные объекты ADO)
title: Метод Жетсчемаобжект (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4031b9dbe100df7e73c64354888ffa97cf38c30c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986695"
---
# <a name="getschemaobject-method-ado-md"></a>Метод GetSchemaObject (многомерные объекты ADO)
Извлекает объект схемы объекты данных ActiveX (MD) ([измерение](./dimension-object-ado-md.md), [иерархию](./hierarchy-object-ado-md.md), [уровень](./level-object-ado-md.md)или [элемент](./member-object-ado-md.md)) по его свойству [UniqueName](./uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjType*  
 Значение [счемаобжекттипинум](./schemaobjecttypeenum.md) , указывающее тип объекта схемы (измерения, иерархии, уровня или элемента), который требуется получить.  
  
 *UniqueName*  
 **Строка** , указывающая значение свойства **UniqueName** получаемого объекта.  
  
## <a name="remarks"></a>Remarks  
 **Жетсчемаобжект** извлекает объекты, используя их уникальные имена, как указано в свойстве **UniqueName** . Имена родительских объектов не обязательно должны быть известны, а для получения объекта схемы не нужно заполнять родительские коллекции.  
  
## <a name="applies-to"></a>Применение  
 [Объект CubeDef (многомерные объекты ADO)](./cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект CubeDef (многомерные объекты ADO)](./cubedef-object-ado-md.md)