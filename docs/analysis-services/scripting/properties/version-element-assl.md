---
title: Элемент Version (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c387686f830fb371b728dfd5c45f22aabaa03560
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="version-element-assl"></a>Элемент Version (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит предназначенную только для чтения версию экземпляра служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , представленного элементом [Server](../../../analysis-services/scripting/objects/server-element-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
      ...  
      <Version>...</Version>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Версии** описывает, какая версия [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] установлен.  
  
 Элемент, соответствующий родителю параметра **версии** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Edition & #40; ASSL & #41;](../../../analysis-services/scripting/properties/edition-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
