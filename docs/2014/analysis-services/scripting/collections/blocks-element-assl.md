---
title: Блокирует элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2776ea261c26bd8c53d3f78ba29231823bb659d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161325"
---
# <a name="blocks-element-assl"></a>Элемент Blocks (ASSL)
  Содержит коллекцию блоков двоичных данных, которые представляют двоичное содержимое [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Данные](../objects/data-element-assl.md) типа [DataBlock](../data-type/datablock-data-type-assl.md)|  
|Дочерние элементы|[Блок](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Blocks` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](files-element-assl.md)   
 [Файл элемента &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Элемент Blocks](blocks-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
