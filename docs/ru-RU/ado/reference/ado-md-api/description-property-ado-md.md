---
title: Свойство Description (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 7136df5847753cded0ed8d735bf64f9d2dc90b79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
|[Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Объект Dimension (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект Hierarchy (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Объект Level (многомерные объекты ADO)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||
