---
title: Элемент FolderPosition (XML) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 8cccef2b-bdd0-415a-bb53-bda14165d1e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86be2c1a79d99fe315ef4baf7157b91107689015
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082974"
---
# <a name="folderposition-element-xml"></a>Элемент FolderPosition (XML)
  Содержит сведения о позиции элемента в коллекции элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <FolderPosition>...</FolderPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|-1|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `RelationshipEndVisualizationProperties` элемент `FolderPosition` содержит положение элемента папки по умолчанию в коллекции папок. Значение по умолчанию, равное `false`, указывает, что папка по умолчанию не используется.  
  
  
