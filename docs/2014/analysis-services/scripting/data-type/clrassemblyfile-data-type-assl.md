---
title: Тип данных ClrAssemblyFile (ASSL) | Документы Microsoft
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
- ClrAssemblyFile Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssemblyFile
helpviewer_keywords:
- ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b542c4193d80fa80cc9aed6663f41e102266000b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096527"
---
# <a name="clrassemblyfile-data-type-assl"></a>Тип данных ClrAssemblyFile (ASSL)
  Определяет тип-примитив, представляющий один из файлов, составляющих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] `Assembly` ([ClrAssembly](assembly-data-type-assl.md) элемент).  
  
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
|Дочерние элементы|[Данные](../objects/data-element-assl.md), [имя](../properties/name-element-assl.md), [типа](../properties/type-element-clrassemblyfile-assl.md)|  
|Производные элементы|[Файл](../objects/file-element-assl.md) ([файлы](../collections/files-element-assl.md) коллекцию [ClrAssembly](assembly-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Элемент Assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Блокирует элемент &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Тип данных ComAssembly &#40;ASSL&#41;](comassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  