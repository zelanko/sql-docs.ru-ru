---
title: Тип данных CubeBinding (вне строки) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeBinding
helpviewer_keywords:
- CubeBinding data type
ms.assetid: 5e1ee8ef-855c-4f3d-ae21-a33360d00d66
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c13cd736887569cfa5fd12bde73e1129e1fd046
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161255"
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>Тип данных CubeBinding (внешний) (ASSL)
  Определяет тип-примитив, представляющий связь между [куба](../objects/cube-element-assl.md) элемент и [DataSource](../objects/datasource-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeBinding>  
   <ID>...</ID>  
   <DataSourceID>...</DataSourceID>  
   <DataSource>...</DataSource>  
   <MeasureGroup>...</MeasureGroup>  
</CubeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Источник данных](../objects/datasource-element-assl.md), [DataSourceID](../properties/id-element-assl.md), [идентификатор](../properties/id-element-assl.md), [MeasureGroup](../objects/group-element-assl.md)|  
|Производные элементы|[Привязка](../../xmla/xml-elements-properties/binding-element-xmla.md) ([привязки](../../xmla/xml-elements-properties/bindings-element-xmla.md) коллекцию [процесс](../../xmla/xml-elements-commands/process-element-xmla.md) или [пакета](../../xmla/xml-elements-commands/batch-element-xmla.md) команд)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о привязках вне строки, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Тип данных Binding &#40;ASSL&#41;](binding-data-type-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
