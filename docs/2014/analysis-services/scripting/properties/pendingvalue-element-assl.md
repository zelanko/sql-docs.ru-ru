---
title: Элемент PendingValue (ASSL) | Документы Microsoft
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
- PendingValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PendingValue
helpviewer_keywords:
- PendingValue element
ms.assetid: 386b2ec6-3d83-42d2-b83a-83e375fbdcbd
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 120c98d128698331a054a89be97ffa1513bb0191
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099877"
---
# <a name="pendingvalue-element-assl"></a>Элемент PendingValue (ASSL)
  Содержит допускающее только чтение отложенное значение связанного [ServerProperty](../objects/serverproperty-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ServerProperty>  
   ...  
   <PendingValue>...</PendingValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой тип simpleType|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент содержит значение `ServerProperty` , которые будут использоваться при следующем запуске текущего экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] запущена. Это значение обычно получается из того же места, где хранится соответствующее значение свойства сервера: из файла инициализации, системного реестра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows или из другого средства хранения данных.  
  
 Элемент, соответствующий родителю параметра `PendingValue` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ServerProperties &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  