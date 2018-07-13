---
title: Тип данных ProactiveCachingBinding (ASSL) | Документация Майкрософт
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
- ProactiveCachingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d440911eefa33981ef435240c4e440378da34a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189101"
---
# <a name="proactivecachingbinding-data-type-assl"></a>Тип данных ProactiveCachingBinding (ASSL)
  Определяет абстрактный производный тип данных, представляющий сведения для [ProactiveCaching](../objects/proactivecaching-element-assl.md) сведения об изменениях в источнике данных, которые требуют перестройки кэша, или о состоянии процесса перестройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|[ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md), [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` тип и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>Иерархия наследования типов данных ProactiveCachingBinding  
 Следующая иерархия показывает наследование типов данных `ProactiveCachingBinding`.  
  
 [Привязка](binding-data-type-assl.md) элемент  
  
 Элемент `ProactiveCachingBinding`  
  
 [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md) элемент  
  
 [ProactiveCachingQueryBinding](querybinding-data-type-assl.md) элемент  
  
 [ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md) элемент  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
