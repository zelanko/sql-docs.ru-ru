---
title: "Синхронизировать элемент (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Synchronize Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords: Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e3361f8cdd01421561bbb6b16d4b6cf5675a356
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="synchronize-element-xmla"></a>Элемент Synchronize (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Синхронизирует [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных с другой существующей базой данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [расположения](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Команда **Synchronize** синхронизирует целевую базу данных с экземпляром источника и базой данных, указанными в элементе **Source** . По желанию команда **Synchronize** может синхронизировать удаленные секции, определенные в базе данных-источнике.  
  
 В зависимости от режима хранения, используемого для объектов в файле резервной копии, команда **Synchronize** синхронизирует данные так, как это показано в следующей таблице.  
  
|Режим хранения|Сведения|  
|------------------|-----------------|  
|Многомерный OLAP (MOLAP)|Исходные данные, агрегаты и метаданные|  
|Гибридный OLAP (HOLAP)|Агрегаты и метаданные|  
|Реляционный OLAP (ROLAP)|Метаданные|  
  
 Во время выполнения команды **Synchronize** на базу данных-источник ставится блокировка на чтение, а на целевую базу данных — блокировка на запись. Обе блокировки снимаются после выполнения команды **Synchronize** .  
  
 Дополнительные сведения о синхронизации баз данных см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Резервный элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Элемент Batch &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Элемент Parallel &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Восстановить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
