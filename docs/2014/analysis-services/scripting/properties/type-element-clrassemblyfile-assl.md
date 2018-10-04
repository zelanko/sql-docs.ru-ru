---
title: Введите элемент (ClrAssemblyFile) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (ClrAssemblyFile)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f5f52857fd9e87541e07ee03ffd36a7b24a4e96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140384"
---
# <a name="type-element-clrassemblyfile-assl"></a>Элемент Type (ClrAssemblyFile) (ASSL)
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
|Родительский элемент|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Main*|Указанный файл является главным в сборке.|  
|*Зависимые*|Указанный файл является зависимым в сборке.|  
|*Отладка*|Указанный файл содержит сведения для отладки.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Type` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ClrAssemblyFileType>.  
  
 Элемент, соответствующий родителю параметра `Type` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Файл элемента &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Элемент Assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
