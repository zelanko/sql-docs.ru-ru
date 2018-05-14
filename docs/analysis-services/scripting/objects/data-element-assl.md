---
title: Элемент данных (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 697e44fa6defa64165e4b09c96315cb4efa4a0bc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="data-element-assl"></a>Элемент Data (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит (в коллекцию дочерних [блока &#40;ASSL&#41; ](../../../analysis-services/scripting/objects/block-element-assl.md) элементы) двоичное содержимое [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<File xsi:type="ClrAssemblyFile">  
   ...  
   <Data xsi:type="DataBlock">...</Data>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataBlock](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Файл](../../../analysis-services/scripting/objects/file-element-assl.md) типа [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра **данные** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Элемент Blocks & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
