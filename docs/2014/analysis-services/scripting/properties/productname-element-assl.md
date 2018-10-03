---
title: Элемент ProductName (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProductName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProductName
helpviewer_keywords:
- ProductName element
ms.assetid: f8129bb2-55c9-44e1-8857-82dc01c04a7f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959f6624e0ce22647f724279042f5cd6ab6ba2f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149894"
---
# <a name="productname-element-assl"></a>Элемент ProductName (ASSL)
  Содержит название продукта, доступный только для чтения экземпляра класса [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , связанный с [Server](../objects/server-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
      ...  
      <ProductName>...</ProductName>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Server](../objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `ProductName` предоставляет доступ только для чтения к имени продукта, связанного с экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Элемент, соответствующий родителю параметра `ProductName` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
