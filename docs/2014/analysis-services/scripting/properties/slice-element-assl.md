---
title: Выполните срез элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Slice Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Slice
helpviewer_keywords:
- Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84bcab815ec93feae3b997c0341bb8c59012cb17
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169734"
---
# <a name="slice-element-assl"></a>Элемент Slice (ASSL)
  Содержит многомерное выражение, которое определяет срез, содержащийся в секции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
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
|Родительский элемент|[Секция](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Slice` содержит многомерное выражение кортежа или выражение набора, обозначающее ту часть куба, информация для которой хранится в секции. Многомерное выражение аналогично [StrToSet](/sql/mdx/strtoset-mdx) MDX-функцию с ключевым словом CONSTRAINED тем, что выражение не может включать Многомерные или определяемые пользователем функции.  
  
 Элемент, соответствующий родителю параметра `Slice` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
