---
title: Тип данных TimeAttributeBinding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TimeAttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TimeAttributeBinding
helpviewer_keywords:
- TimeAttributeBinding data type
ms.assetid: e8317b1c-a83a-4074-9538-400792500985
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be0089d7a90ee181a67f84cb204751879453ba5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113534"
---
# <a name="timeattributebinding-data-type-assl"></a>Тип данных TimeAttributeBinding (ASSL)
  Определяет производный тип данных, представляющий «заполнитель» привязки для созданных элементов данных, например для ключевых столбцов атрибута в серверном измерении времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TimeAttributeBinding>  
   <!-- TimeAttributeBinding has no child elements other than those inherited from Binding -->  
</TimeAttributeBinding>  
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
|Дочерние элементы|None|  
|Производные элементы|См. в разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` тип и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.TimeAttributeBinding>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
