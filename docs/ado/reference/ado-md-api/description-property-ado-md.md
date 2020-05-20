---
title: Свойство Description (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 05efe4c1e31f1ee9c7b7abd130a9d9c810ab12f4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764315"
---
# <a name="description-property-ado-md"></a>Свойство Description (многомерные объекты ADO)
Возвращает текстовое описание текущего объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строку** и доступна только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Для объектов [member](../../../ado/reference/ado-md-api/member-object-ado-md.md) **Описание** применяется только к элементам Measure и формуле. **Описание** возвращает пустую строку ("") для всех других типов элементов. Дополнительные сведения о различных типах членов см. в описании свойства [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) .  
  
 Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект CubeDef (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Объект Dimension (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Объект Hierarchy (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Объект Level (многомерные объекты ADO)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||
