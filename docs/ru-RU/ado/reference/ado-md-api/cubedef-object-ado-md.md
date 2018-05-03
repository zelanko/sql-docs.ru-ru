---
title: Объект CubeDef (ADO MD) | Документы Microsoft
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
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8144c74fb0229e334b5ff6bee5b94c716624dc76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cubedef-object-ado-md"></a>Объект CubeDef (ADO MD)
Представляет куб из многомерной схемой, содержащий набор связанных измерений.  
  
## <a name="remarks"></a>Замечания  
 С коллекциями и свойствами **CubeDef** объекта, можно сделать следующее:  
  
-   Определить **CubeDef** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) свойства.  
  
-   Возвращает строку, описывающую куба с помощью [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Возвращает измерения, входящие в состав куба с помощью [измерения](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) коллекции.  
  
-   Получить дополнительные сведения о **CubeDef** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Название|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CreatedOn|Дата и время создания куба.|  
|CubeGUID|Куб GUID.|  
|CubeName|Имя куба.|  
|CubeType|Тип куба.|  
|DataUpdatedBy|Идентификатор пользователя, пользователь, выполняющий последнего обновления данных.|  
|Описание|Понятное описание куба.|  
|LastSchemaUpdate|Дата и время последнего обновления схемы.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
|SchemaUpdatedBy|Идентификатор пользователя, пользователь, выполняющий последнее обновление схемы.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект каталога (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Коллекция CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Коллекции измерений (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
