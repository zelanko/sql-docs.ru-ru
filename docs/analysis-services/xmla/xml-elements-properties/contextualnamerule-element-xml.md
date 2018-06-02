---
title: Элемент ContextualNameRule (XML) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b2c49f32029078bbe67e70066845f5b8f7d4f3c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573516"
---
# <a name="contextualnamerule-element-xml"></a>Элемент ContextualNameRule (XML)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит указание по наилучшему способу создания составного имени для атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <ContextualNameRule>...</ContextualNameRule>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|-1|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Содержит указание для клиентских приложений по созданию однозначных имен для этого атрибута.  
  
 Значением элемента **ContextualNameRule** может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*None*|Используется имя атрибута.|  
|*Контекст*|Используется имя входящей связи.|  
|*Объединить*|В соответствии с правилами языка приложения имя входящей связи объединяется с именем атрибута.|  
  
  
