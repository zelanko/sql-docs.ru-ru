---
title: Имя свойства (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c248139abfd136d5c79658592e0e49d5e10444aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949397"
---
# <a name="name-property-ado-md"></a>Свойство Name (многомерные объекты ADO)
Указывает имя объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строка** и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Вы можете получить **имя** свойства объекта с порядковым номером, после чего можно ссылаться на объект непосредственно по имени. Например если `cdf.CubeDefs(0).Name` дает «Bobs видео Store», можно ссылаться на это [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) как `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Объект Catalog (многомерные объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Объект Dimension (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект Hierarchy (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Объект Level (многомерные объекты ADO)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (Visual Basic)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Свойство Caption (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Свойство Description (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Свойство UniqueName (многомерные объекты ADO)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
