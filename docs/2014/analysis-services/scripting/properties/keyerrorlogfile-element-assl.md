---
title: Элемент KeyErrorLogFile (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyErrorLogFile Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyErrorLogFile
helpviewer_keywords:
- KeyErrorLogFile element
ms.assetid: 1455bb54-03f7-4f25-9d4d-ab75231dd958
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3387498c26e0bf690b2934ea9e1ee99107414c04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094838"
---
# <a name="keyerrorlogfile-element-assl"></a>Элемент KeyErrorLogFile (ASSL)
  Содержит имя файла для ведения журнала ошибок обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
   ...  
</ErrorConfiguration>  
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
|Родительский элемент|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `KeyErrorLogFile` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorConfiguration>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  