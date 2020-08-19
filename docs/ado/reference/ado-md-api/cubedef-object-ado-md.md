---
description: Объект CubeDef (многомерные объекты ADO)
title: Объект CubeDef (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: cf8de68674ee1cc33f0ba16c9a0b3604418d0332
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441156"
---
# <a name="cubedef-object-ado-md"></a>Объект CubeDef (многомерные объекты ADO)
Представляет куб из многомерной схемы, содержащий набор связанных измерений.  
  
## <a name="remarks"></a>Комментарии  
 С помощью коллекций и свойств объекта **CubeDef** можно выполнять следующие действия.  
  
-   Найдите **CubeDef** с помощью свойства [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) .  
  
-   Возвращает строку, описывающую куб со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Возвращает измерения, которые составляют куб, с помощью коллекции [измерений](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) .  
  
-   Получите дополнительные сведения о **CubeDef** со стандартной коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO.  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CreatedOn|Дата и время создания куба.|  
|кубегуид|GUID Куба.|  
|CubeName|Имя куба.|  
|кубетипе|Тип куба.|  
|датаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление данных.|  
|Описание|Понятное описание Куба.|  
|LastSchemaUpdate|Дата и время последнего обновления схемы.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
|счемаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление схемы.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект каталога (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Коллекция Кубедефс (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Коллекция Dimensions (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
