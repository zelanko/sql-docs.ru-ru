---
title: Элемент Data (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Data Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Data
helpviewer_keywords:
- Data element
ms.assetid: e52b1961-7e11-4029-8ab1-84d275845067
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57958cfe25563b4a7e2fd53f639d3bc289dce07c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117371"
---
# <a name="data-element-assl"></a>Элемент Data (ASSL)
  Содержит (в коллекции дочерних [блока &#40;ASSL&#41; ](block-element-assl.md) элементы) двоичное содержимое [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемент.  
  
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
|Тип данных и длина|[DataBlock](../data-type/datablock-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Файл](file-element-assl.md) типа [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `Data` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Блокирует элемент &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
