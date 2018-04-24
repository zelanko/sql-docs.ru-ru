---
title: Имя свойства (ADO MD) | Документы Microsoft
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
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95feb68ff0e1b11d9c51590304c254940036c4be
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="name-property-ado-md"></a>Свойство Name (ADO MD)
Указывает имя объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строка** и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Вы можете получить **имя** свойство объекта по порядковому номеру, после чего можно ссылаться на объект напрямую по имени. Например если `cdf.CubeDefs(0).Name` дает «Bobs видео Store», можно ссылаться на это [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) как `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Объект Catalog (многомерные объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Объект Dimension (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект Hierarchy (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Объект Level (многомерные объекты ADO)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (Visual Basic)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Свойство Caption (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Свойство Description (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Свойство UniqueName (многомерные объекты ADO)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
