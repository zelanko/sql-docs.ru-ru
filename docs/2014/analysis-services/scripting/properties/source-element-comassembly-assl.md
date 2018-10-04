---
title: Исходный элемент (ComAssembly) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (ComAssembly)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 5c9209e8-ace6-4688-a64d-4987a7648ab9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7c6259d5bec6c2c1e371df5d9412ccdbc5489a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106514"
---
# <a name="source-element-comassembly-assl"></a>Элемент Source (ComAssembly) (ASSL)
  Содержит имя файла или программный идентификатор (ProgID) для COM-компонента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ComAssembly>  
   ...  
   <Source>...</Source>  
   ...  
</ComAssembly>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ComAssembly](../data-type/assembly-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Source` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/clrassembly-data-type-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Элемент Database описания &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
