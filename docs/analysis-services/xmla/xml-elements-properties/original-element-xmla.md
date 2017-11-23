---
title: "Элемент Original (XML для Аналитики) | Документы Microsoft"
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
apiname: Original Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords: Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 352a4fd4e4be62a666acdc384379ce45c90ee915
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="original-element-xmla"></a>Элемент Original (XML для аналитики)
  Содержит исходное место хранения файловой системе используется [папки](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папка](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Исходного** элемент содержит UNC-путь, чтобы заменить значение [New](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) элемента, содержащегося в родительском **папки** элемент для всех объектов, восстановить или синхронизированные, соответственно, во время [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды. Значение этого элемента сравнивается значение [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) элемент для каждого куба, группы мер или секции и, если найдено совпадение, значение **New** элемент используется для обновления  **StorageLocation** объекта во время восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
