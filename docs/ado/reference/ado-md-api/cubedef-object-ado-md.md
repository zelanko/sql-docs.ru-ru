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
ms.openlocfilehash: f2a25f9a964e6a8e9644eb737897dd15e3948974
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778263"
---
# <a name="cubedef-object-ado-md"></a>Объект CubeDef (многомерные объекты ADO)
Представляет куб из многомерной схемы, содержащий набор связанных измерений.  
  
## <a name="remarks"></a>Remarks  
 С помощью коллекций и свойств объекта **CubeDef** можно выполнять следующие действия.  
  
-   Найдите **CubeDef** с помощью свойства [Name](./name-property-ado-md.md) .  
  
-   Возвращает строку, описывающую куб со свойством [Description](./description-property-ado-md.md) .  
  
-   Возвращает измерения, которые составляют куб, с помощью коллекции [измерений](./dimensions-collection-ado-md.md) .  
  
-   Получите дополнительные сведения о **CubeDef** со стандартной коллекцией [свойств](../ado-api/properties-collection-ado.md) ADO.  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Название|Описание:|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CreatedOn|Дата и время создания куба.|  
|кубегуид|GUID Куба.|  
|CubeName|Имя куба.|  
|кубетипе|Тип куба.|  
|датаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление данных.|  
|Описание:|Понятное описание Куба.|  
|LastSchemaUpdate|Дата и время последнего обновления схемы.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
|счемаупдатедби|Идентификатор пользователя, выполняющего Последнее обновление схемы.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](./cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](./cubedef-example-vbscript.md)   
 [Объект каталога (объекты данных ActiveX (MD))](./catalog-object-ado-md.md)   
 [Коллекция Кубедефс (объекты данных ActiveX (MD))](./cubedefs-collection-ado-md.md)   
 [Коллекция Dimensions (объекты данных ActiveX (MD))](./dimensions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)