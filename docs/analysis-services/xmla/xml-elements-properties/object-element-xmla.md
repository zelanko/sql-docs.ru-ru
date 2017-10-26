---
title: "Объект элемента (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Object Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: 99470537-2c4a-4072-9613-940c41c12487
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ea187bdeebdfeeb64eb2ff379181f1a03783afa8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="object-element-xmla"></a>Элемент Object (XML для аналитики)
  Содержит ссылку на объект, которая используется родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <!-- One or more object identifiers, depending on the parent element -->  
   </Object>  
...  
</Alter>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|См. в следующей таблице.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[ALTER](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|0—1: необязательный элемент, который может появляться только один раз.|  
|Все остальные|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ALTER](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [удаление](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [блокировки](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [подписаться](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [синхронизации](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|Обязательные элементы языка ASSL. Указывается перечислением элементов ID объекта и его предков (исключая **сервера** объекта.) Например, следующая **объекта** определяет секцию:<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Замечания  
 Порядок следования идентификаторов неважен.  
  
 Для **Alter** элементов, экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используется как объект по умолчанию, если **объекта** элемент не указан.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

