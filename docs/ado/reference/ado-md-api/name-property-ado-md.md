---
description: Свойство Name (многомерные объекты ADO)
title: Свойство Name (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfec86bb631dda661b957e02667cd320c20fec6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986245"
---
# <a name="name-property-ado-md"></a>Свойство Name (многомерные объекты ADO)
Указывает имя объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строку** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Name** объекта можно получить по порядковому номеру, после чего можно будет ссылаться на объект непосредственно по имени. Например, если `cdf.CubeDefs(0).Name` выдает "bobs Video Store", можно ссылаться на этот [CubeDef](./cubedef-object-ado-md.md) как `cdf.CubeDefs("Bobs Video Store")` .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Axis (многомерные объекты ADO)](./axis-object-ado-md.md)  
        [Объект Catalog (многомерные объекты ADO)](./catalog-object-ado-md.md)  
        [Объект CubeDef (многомерные объекты ADO)](./cubedef-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Объект Dimension (многомерные объекты ADO)](./dimension-object-ado-md.md)  
        [Объект Hierarchy (многомерные объекты ADO)](./hierarchy-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Объект Level (многомерные объекты ADO)](./level-object-ado-md.md)  
        [Объект Member (многомерные объекты ADO)](./member-object-ado-md.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример каталога (VB)](./catalog-example-vb.md)   
 [Свойство Caption (объекты данных ActiveX (MD))](./caption-property-ado-md.md)   
 [Свойство Description (объекты данных ActiveX (MD))](./description-property-ado-md.md)   
 [Свойство UniqueName (многомерные объекты ADO)](./uniquename-property-ado-md.md)