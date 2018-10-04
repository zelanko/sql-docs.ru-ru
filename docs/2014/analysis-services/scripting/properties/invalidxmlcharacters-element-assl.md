---
title: Элемент InvalidXmlCharacters (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- InvalidXmlCharacters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- InvalidXmlCharacters
helpviewer_keywords:
- InvalidXmlCharacters element
ms.assetid: 92b1210c-1075-4f2f-a2c4-dfdc6d7e5c05
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0832f4138adc3f278af0d735b70251590fb3ba41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059646"
---
# <a name="invalidxmlcharacters-element-assl"></a>Элемент InvalidXmlCharacters (ASSL)
  Определяет метод обработки неправильных символов XML в исходных данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
   ...  
</DataItem  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Сохранить*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Сохранить*|Недопустимые XML-символы сохраняются.|  
|*Удалить*|Недопустимые XML-символы удаляются.|  
|*Заменить*|Недопустимые XML-символы заменяются символами знака вопроса (?).|  
  
 Перечисление, соответствующее допустимым значениям элемента `InvalidXmlCharacters` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.InvalidXmlCharacters>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
