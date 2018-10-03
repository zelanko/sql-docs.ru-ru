---
title: Элемент DataSourceID (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.datasourceid
- urn:schemas-microsoft-com:xml-analysis#DataSourceID
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 695522c7-acca-420a-a5fb-f01f3fd9a96b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2a403655594027599d56490c6bd2456c0713bf34
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099451"
---
# <a name="datasourceid-element-xmla"></a>Элемент DataSourceID (XML для аналитики)
  Определяет источник данных, используемые [расположение](location-element-xmla.md) во время выполнения [резервного копирования](../xml-elements-commands/backup-element-xmla.md), [восстановить](../xml-elements-commands/restore-element-xmla.md), или [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location>  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Расположение](location-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `DataSourceID` содержит имя источника данных на исходном экземпляре, позволяющее определить удаленный экземпляр для резервного копирования, восстановления или синхронизации сведений удаленной секции.  
  
 Дополнительные сведения о резервном копировании и восстановлении удаленных секций, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент ConnectionString &#40;XML для Аналитики&#41;](connectionstring-element-xmla.md)   
 [Элемент DataSourceType &#40;XML для Аналитики&#41;](type-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
