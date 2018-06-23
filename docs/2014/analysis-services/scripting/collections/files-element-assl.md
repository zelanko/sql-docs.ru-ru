---
title: Файлы элемент (ASSL) | Документы Microsoft
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
- Files Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5f7556009881e1d4155e47a368bcff4b49aa7988
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097622"
---
# <a name="files-element-assl"></a>Элемент Files (ASSL)
  Содержит коллекцию элементов [файл](../objects/file-element-assl.md) элементов, составляющих [ClrAssembly](../data-type/assembly-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
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
|Родительские элементы|[Сборка](../objects/assembly-element-assl.md) типа [ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Дочерние элементы|[Файл](../objects/file-element-assl.md) типа [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)   
 [Элемент данных &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Блокирует элемент &#40;ASSL&#41;](blocks-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Тип данных ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  