---
title: "Имя свойства (ADO MD) | Документы Microsoft"
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
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d898b2e478b9a5dfccb431d0d29088c9e8d9286
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
|[Объект Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Объект каталога (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Объект CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Объект измерения (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект иерархии (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Объект уровня (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Объект члена (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>См. также:  
 [Пример каталога (Visual Basic)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Свойство Caption (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Свойство Description (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Свойство UniqueName (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)

