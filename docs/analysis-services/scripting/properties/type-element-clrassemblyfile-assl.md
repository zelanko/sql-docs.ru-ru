---
title: Введите элемент (ClrAssemblyFile) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element (ClrAssemblyFile)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 627f8aecd46442088e9fb7b6581682ab5fd4c4f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="type-element-clrassemblyfile-assl"></a>Элемент Type (ClrAssemblyFile) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Задает тип файла одного из файлов, принадлежащих к [!INCLUDE[msCoName](../../../includes/msconame-md.md)] сборки .NET Framework.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClrAssemblyFile>  
      ...  
      <Type>...</Type>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Main*|Указанный файл является главным в сборке.|  
|*Зависимые*|Указанный файл является зависимым в сборке.|  
|*Отладка*|Указанный файл содержит сведения для отладки.|  
  
 Перечисление, соответствующее разрешенным значениям для **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент файла & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Элемент Assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
