---
title: Элемент Folder (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Folder Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.folder
- http://schemas.microsoft.com/analysisservices/2003/engine#Folder
- urn:schemas-microsoft-com:xml-analysis#Folder
helpviewer_keywords:
- Folder element
ms.assetid: 87b305b0-57e3-4ec3-9d80-f1bcf3ce7540
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: adff40aaff133b372b1407d3672ebba0fa371136
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="folder-element-xmla"></a>Элемент Folder (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит место хранения файловой системы должны быть обновлены в [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) во время выполнения [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папки](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Дочерние элементы|[Новый](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [исходного](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 При указании элемента **Folder** он изменяет места хранения объектов, содержащихся в файле резервной копии (для команд **Restore** ) или в базе данных на экземпляре источника (для команд **Synchronize** ), если их значения совпадают со значением элемента **Original** . Каждое такое значение заменяется значением элемента **New** .  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование, восстановление и синхронизация баз данных & #40; XML для Аналитики & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент StorageLocation & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
