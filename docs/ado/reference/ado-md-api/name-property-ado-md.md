---
title: Свойство Name (объекты данных ActiveX (MD)) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949397"
---
# <a name="name-property-ado-md"></a>Свойство Name (многомерные объекты ADO)
Указывает имя объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строку** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Name** объекта можно получить по порядковому номеру, после чего можно будет ссылаться на объект непосредственно по имени. Например, если `cdf.CubeDefs(0).Name` выдает "bobs Video Store", можно ссылаться на этот [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) как `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Объект Catalog (многомерные объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Объект Dimension (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект Hierarchy (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Объект Level (многомерные объекты ADO)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>См. также:  
 [Пример каталога (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Свойство Caption (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Свойство Description (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [Свойство UniqueName (многомерные объекты ADO)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
