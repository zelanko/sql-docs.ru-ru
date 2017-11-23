---
title: "Элемент ConnectionString (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ConnectionString Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords: ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 435d5d141652c4f043043fd26c85b9cb9a29f040
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="connectionstring-element-xmla"></a>Элемент ConnectionString (XML для аналитики)
  Содержит строку соединения, используемой родительским [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) или [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|См. в следующей таблице.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Местоположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для **расположение** элементов, **ConnectionString** элемент содержит строку подключения, используемые **восстановить** или **Synchronize** Команда обновить локальный источник данных или подключиться к удаленному экземпляру.  
  
 Для **источника** элементов, **ConnectionString** элемент содержит строку подключения, используемые **Synchronize** команду, чтобы соединиться с экземпляром источника.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Восстановить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Синхронизировать элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
