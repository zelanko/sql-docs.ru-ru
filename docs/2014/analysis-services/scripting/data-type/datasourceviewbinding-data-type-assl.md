---
title: Тип данных DataSourceViewBinding (ASSL) | Документы Microsoft
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
- DataSourceViewBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataSourceViewBinding
helpviewer_keywords:
- DataSourceViewBinding data type
ms.assetid: 1f08e2d8-b279-4181-9257-e56f9fcbd9bf
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 68b2a967fc57187d343a8cfd06e5706f474ab90d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193688"
---
# <a name="datasourceviewbinding-data-type-assl"></a>Тип данных DataSourceViewBinding (ASSL)
  Определяет производный тип данных, представляющий привязку представления источников данных к родительскому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSourceViewBinding>  
   <!-- The following elements extend Binding -->  
   <DataSourceViewID>...</DataSourceViewID>  
</DataSourceViewBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[DataSourceViewID](../properties/id-element-assl.md)|  
|Производные элементы|В разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) `Binding` тип и иерархию наследования `Binding` типов, в разделе [тип привязки данных &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DataSourceViewBinding>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  