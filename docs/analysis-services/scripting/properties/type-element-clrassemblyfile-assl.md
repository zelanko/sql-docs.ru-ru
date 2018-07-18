---
title: Введите элемент (ClrAssemblyFile) (ASSL) | Документация Майкрософт
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a4cf5d0a1ef4fd627dd10d0b73ca1520980484fe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990306"
---
# <a name="type-element-clrassemblyfile-assl"></a>Элемент Type (ClrAssemblyFile) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает тип файла одного из файлов, принадлежащих к [!INCLUDE[msCoName](../../../includes/msconame-md.md)] сборки .NET Framework.  
  
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
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Main*|Указанный файл является главным в сборке.|  
|*Зависимые*|Указанный файл является зависимым в сборке.|  
|*Отладка*|Указанный файл содержит сведения для отладки.|  
  
 Перечисление, соответствующее допустимым значениям для **тип** в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 Элемент, соответствующий родителю параметра **тип** в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Файл элемента &#40;ASSL&#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Элемент Assembly &#40;ASSL&#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
