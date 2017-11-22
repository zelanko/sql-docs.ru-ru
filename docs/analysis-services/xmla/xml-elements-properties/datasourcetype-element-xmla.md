---
title: "Элемент DataSourceType (XML для Аналитики) | Документы Microsoft"
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
apiname: DataSourceType Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords: DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0474881e6ca90b395bd908a8e152688b8784557b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="datasourcetype-element-xmla"></a>Элемент DataSourceType (XML для аналитики)
  Указывает ли [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) элемент, указанный для [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команда является локальным или удаленным.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Удаленный*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Местоположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **DataSourceType** определяет, содержит ли элемент **Location** локальный или удаленный источник данных. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Локальные*|Элемент **Location** определяет локальный источник данных. При использовании этого значения команды **Restore** и **Synchronize** используют определенные в элементе **Location** сведения для обновления источника данных, полученного или из файлов резервной копии, заданной в элементе **File** для команды **Backup** , или из базы данных, заданной в элементе **Source** для команды **Synchronize** . Источник данных определяется элементом **DataSourceID** элемента **Location** .<br /><br /> Это значение позволяет объектам, пользующимся реляционным хранилищем OLAP (ROLAP), после восстановления или синхронизации использовать другую базу данных для хранения данных и метаданных.<br /><br /> Примечание: Данные ROLAP, например данных в таблицах измерения или таблицах обратной записи, не восстанавливаются и синхронизируются. Восстанавливаются и синхронизируются только метаданные объектов ROLAP.|  
|*Удаленный*|Элемент **Location** определяет удаленный источник данных. При использовании этого значения команды **Restore** и **Synchronize** используют определенные в элементе **Location** сведения для восстановления или синхронизации в удаленном экземпляре, определенном элементом **File** элемента **Backup** , удаленных секций, полученных или из файлов резервной копии, заданной в элементе **Source** для команды **Synchronize** , или из базы данных, заданной в элементе **DataSourceID** для команды **Location** .|  
  
## <a name="see-also"></a>См. также:  
 [Элемент ConnectionString &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Элемент DataSourceID &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
