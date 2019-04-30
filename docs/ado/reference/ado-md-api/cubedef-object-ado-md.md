---
title: Объект CubeDef (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1027fc76cb09f7b846e1b8edad52a3cb5dbf2bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225909"
---
# <a name="cubedef-object-ado-md"></a>Объект CubeDef (многомерные объекты ADO)
Представляет куб из многомерной схемой, содержащий набор связанных измерений.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств **CubeDef** объекта, можно сделать следующее:  
  
-   Определить **CubeDef** с [имя](../../../ado/reference/ado-md-api/name-property-ado-md.md) свойство.  
  
-   Возвращает строку, описывающую куба с [описание](../../../ado/reference/ado-md-api/description-property-ado-md.md) свойство.  
  
-   Возвращает измерения, составляющих куба с [измерения](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) коллекции.  
  
-   Получить дополнительную информацию о **CubeDef** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, к которому принадлежит этот куб.|  
|CreatedOn|Дата и время создания куба.|  
|CubeGUID|Куб GUID.|  
|CubeName|Имя куба.|  
|CubeType|Тип куба.|  
|DataUpdatedBy|Идентификатор пользователя пользователь, выполняющий последнего обновления данных.|  
|Описание|Понятное описание куба.|  
|LastSchemaUpdate|Дата и время последнего обновления схемы.|  
|SchemaName|Имя схемы, которой принадлежит этот куб.|  
|SchemaUpdatedBy|Идентификатор пользователя пользователь, выполняющий последнее обновление схемы.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект каталога (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Коллекция CubeDefs (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Коллекция Dimensions (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
