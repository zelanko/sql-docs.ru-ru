---
title: Тип данных ClrAssemblyFile (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db7ec0dea32fd0fbe0c0584b75fb42b783629daa
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="clrassemblyfile-data-type-assl"></a>Тип данных ClrAssemblyFile (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет тип-примитив, представляющий один из файлов, составляющих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **сборки** ([ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) элемент).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClrAssemblyFile>  
   <Name>...</Name>  
      <Type>...</Type>  
      <Data>...</Data>  
</ClrAssemblyFile>  
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
|Дочерние элементы|[Данные](../../../analysis-services/scripting/objects/data-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [типа](../../../analysis-services/scripting/properties/type-element-clrassemblyfile-assl.md)|  
|Производные элементы|[Файл](../../../analysis-services/scripting/objects/file-element-assl.md) ([файлы](../../../analysis-services/scripting/collections/files-element-assl.md) коллекцию [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Элемент Assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Тип данных DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Элемент Blocks & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Блокировать элемент & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Тип данных ComAssembly & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
