---
title: Тип данных DrillThroughAction (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DrillThroughAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DrillThroughAction
helpviewer_keywords:
- DrillThroughAction data type
ms.assetid: e212d575-a0d7-4548-92b4-33542ef59034
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6a1ccdedbcb1b70e9673afe687a62f95065c3aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219394"
---
# <a name="drillthroughaction-data-type-assl"></a>Тип данных DrillThroughAction (ASSL)
  Определяет производный тип данных, представляющий действие детализации.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DrillThroughAction>  
   <!-- The following elements extend Action -->  
   <Default>...</Default>  
   <Columns>...</Columns>  
</DrillThroughAction>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Действие](action-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Столбцы](../collections/columns-element-assl.md), [по умолчанию](../properties/default-element-assl.md)|  
|Производные элементы|[Действие](../objects/action-element-assl.md) ([действия](../collections/actions-element-assl.md), коллекцию [куба](../objects/cube-element-assl.md), или [перспективы](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DrillThroughAction>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
