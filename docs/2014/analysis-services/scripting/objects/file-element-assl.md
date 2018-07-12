---
title: Файл элемента (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- File
helpviewer_keywords:
- File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03b78545b1df04192a69dffa1a49733509b99700
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155356"
---
# <a name="file-element-assl"></a>Элемент File (ASSL)
  Определяет один из файлов, составляющих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../data-type/assembly-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Файлы](../collections/files-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Files` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server &#40;ASSL&#41;](server-element-assl.md)   
 [Элемент Database описания &#40;ASSL&#41;](database-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Элемент Assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Элемент данных &#40;ASSL&#41;](data-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Блокирует элемент &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](block-element-assl.md)   
 [Тип данных ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
