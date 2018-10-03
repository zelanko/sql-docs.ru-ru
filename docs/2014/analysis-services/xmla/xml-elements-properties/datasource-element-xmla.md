---
title: Элемент DataSource (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSource Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSource
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSource
- microsoft.xml.analysis.datasource
helpviewer_keywords:
- DataSource element
ms.assetid: adc0713a-3927-40f3-8b87-012130908f34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3acbba2e1ee5df1535799e133c064b90b6921386
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130533"
---
# <a name="datasource-element-xmla"></a>Элемент DataSource (XML для аналитики)
  Содержит привязку к источнику данных вне строки для родительского [пакета](../xml-elements-commands/batch-element-xmla.md) или [процесс](../xml-elements-commands/process-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Batch> <!-- or Process>  
...  
   <DataSource>  
      <DatabaseID>...</DatabaseID>  
      <DataSourceID>...</DataSourceID>  
   </DataSource>  
...  
</Batch>  
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
|Родительские элементы|[Batch](../xml-elements-commands/batch-element-xmla.md), [Process](../xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|[DatabaseID](id-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `DataSource` Представляет собой вне строки привязку к источнику данных, используемые `Batch` или `Process` для временного переопределения привязки источника данных для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов, обрабатываемых команда.  
  
 Дополнительные сведения о привязках вне строки, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
