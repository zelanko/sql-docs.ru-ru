---
title: Элемент Parameters (XML для Аналитики) | Документы Microsoft
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
- Parameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 63d50c1b57691a9b4cdb76adb9edaa202388d15e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110230"
---
# <a name="parameters-element-xmla"></a>Элемент Parameters (XML для аналитики)
  Содержит коллекцию элементов [Parameter](parameter-element-xmla.md) , используемых методом [Execute](../xml-elements-methods-execute.md) .  
  
 **Пространство имен:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Выполнение](../xml-elements-methods-execute.md)|  
|Дочерние элементы|[Параметр](parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для некоторых команд (XML для аналитики), таких как [Process](../xml-elements-commands/process-element-xmla.md) , могут потребоваться дополнительные данные. Элемент `Parameters` обеспечивает механизм предоставления дополнительных данных, включая сведения о фрагментах, для команд XMLA.  
  
 Если в команде XML для аналитики элемент `Parameters` не используется, то при вызове метода `Execute` его можно опустить.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  