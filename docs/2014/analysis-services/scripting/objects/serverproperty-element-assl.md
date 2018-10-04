---
title: Элемент ServerProperty (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ServerProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SERVERPROPERTY
helpviewer_keywords:
- ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d84d9fc4bb78969265399d2a67207ea15e753f39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185774"
---
# <a name="serverproperty-element-assl"></a>Элемент ServerProperty (ASSL)
  Определяет свойство сервера, связанное с [Server](server-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ServerProperties](../collections/serverproperties-element-assl.md)|  
|Дочерние элементы|[DefaultValue](../properties/value-element-assl.md), [DisplayFlag](../properties/displayflag-element-assl.md), [имя](../properties/name-element-assl.md), [PendingValue](../properties/pendingvalue-element-assl.md), [RequiresRestart](../properties/requiresrestart-element-assl.md), [значение](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 `ServerProperty` Элемент описывает данные и метаданные для свойства сервера, связанного с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В отличие от элементов, содержащихся в языке сценариев служб Analysis Services (ASSL), элемент `ServerProperty` для описания свойств сервера использует пары «имя-значение», а не явно поименованные свойства. Пары «имя-значение» обеспечивают гибкость применения и расширяемость.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server &#40;ASSL&#41;](server-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
