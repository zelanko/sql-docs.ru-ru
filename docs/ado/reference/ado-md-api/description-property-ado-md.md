---
title: "Свойство Description (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5bc33e6d2e82fc2b74fba7e250cc0b0fd3307ea2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="description-property-ado-md"></a>Свойство Description (ADO MD)
Возвращает текстовое описание текущего объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строка** и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Для [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов, **описание** применяется только к меры и формулы элементов. **Описание** возвращает пустую строку ("») для всех других типов элементов. Дополнительные сведения о различных типах элементов см. в разделе [тип](../../../ado/reference/ado-md-api/type-property-ado-md.md) свойства.  
  
 Это свойство поддерживается только на **член** объектов, принадлежащих [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при обращении к этому свойству из **член** объектов, принадлежащих [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Объект измерения (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект иерархии (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Объект уровня (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Объект члена (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||

