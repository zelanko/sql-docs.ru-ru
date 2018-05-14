---
title: Блокирует элемент (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7d4855bd53eaa13cdabe0e9618171bd8fc781f30
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="blocks-element-assl"></a>Элемент Blocks (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит коллекцию блоков двоичных данных, которые представляют двоичное содержимое [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.  
  
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
|Родительские элементы|[Данные](../../../analysis-services/scripting/objects/data-element-assl.md) типа [DataBlock](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|  
|Дочерние элементы|[Блок](../../../analysis-services/scripting/objects/block-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра **блоки** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Элемент файла & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Тип данных DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Элемент Blocks](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Блокировать элемент & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
