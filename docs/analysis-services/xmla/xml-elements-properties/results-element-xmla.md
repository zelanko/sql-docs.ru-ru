---
title: "результаты Element (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- results Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 791512ba71ef92a9e220936b138faf9eff2a4872
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="results-element-xmla"></a>Элемент results (XML для аналитики)
  Содержит коллекцию элементов [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) , возвращаемых методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) с использованием команды [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) .  
  
 **Пространство имен**`http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Возврат](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Дочерние элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Если команда **Batch** выполняется методом **Execute** , то элемент **return** содержит единственный элемент **results** , а не единственный элемент **root** . Содержимое элемента **results** зависит от параметров, используемых для выполнения команды **Batch** .  
  
 Применительно к командам **Batch** , не входящим в состав транзакции, элемент **results** содержит по одному элементу **root** для каждой команды, выполненной этой командой **Batch** , независимо от того, завершается ли эта команда успешно или неудачно. Применительно к командам **Batch** , входящим в состав транзакции, элемент **results** содержит только один элемент **root** , который содержит информацию об ошибке для команды **Batch** , завершившейся неудачей в составе команды.  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
