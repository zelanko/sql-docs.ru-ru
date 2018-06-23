---
title: результаты Element (XMLA) | Документы Microsoft
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
- results Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 203ad5a79938c80e2bfccc798ff5f9551ac66d8d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100077"
---
# <a name="results-element-xmla"></a>Элемент results (XML для аналитики)
  Содержит коллекцию элементов [root](root-element-xmla.md) , возвращаемых методом [Execute](../xml-elements-methods-execute.md) с использованием команды [Batch](../xml-elements-commands/batch-element-xmla.md) .  
  
 **Пространство имен** http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
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
|Родительские элементы|[Возврат](return-element-xmla.md)|  
|Дочерние элементы|[корень](root-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Если команда `Batch` выполняется методом `Execute`, то элемент `return` содержит единственный элемент `results`, а не единственный элемент `root`. Содержимое элемента `results` зависит от параметров, используемых для выполнения команды `Batch`.  
  
 Применительно к командам `Batch`, не входящим в состав транзакции, элемент `results` содержит по одному элементу `root` для каждой команды, выполненной этой командой `Batch`, независимо от того, завершается ли эта команда успешно или неудачно. Применительно к командам `Batch`, входящим в состав транзакции, элемент `results` содержит только один элемент `root`, который содержит информацию об ошибке для команды `Batch`, завершившейся неудачей в составе команды.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  