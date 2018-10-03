---
title: Элемент Original (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Original Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b09f2388c47206b1b879a5c8dc98f10a28675342
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212074"
---
# <a name="original-element-xmla"></a>Элемент Original (XML для аналитики)
  Содержит исходное место в файловой системе хранилища используется [папку](folder-element-xmla.md) элемент.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папка](folder-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `Original` Элемент содержит UNC-пути заменяется значение [New](new-element-xmla.md) элемента, содержащегося в родительском `Folder` элемент для всех объектов, восстановленных или синхронизированных соответственно, во время [восстановления ](../xml-elements-commands/restore-element-xmla.md) или [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) команды. Значение этого элемента сравнивается значение [StorageLocation](../../scripting/properties/storagelocation-element-assl.md) элемент для каждого куба, группы мер или секции и, если найдено, значение `New` элемент используется для обновления `StorageLocation` из объект во время восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
