---
title: Элемент Original (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0ddf701f236e66680f562fa0721bcc8a2eb179f8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050392"
---
# <a name="original-element-xmla"></a>Элемент Original (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит исходное место в файловой системе хранилища используется [папку](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папка](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Исходного** элемент содержит UNC-пути заменяется значение [New](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) элемента, содержащегося в родительском **папку** элемент для всех объектов, восстановить или синхронизированные, соответственно, во время [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды. Значение этого элемента сравнивается значение [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) элемент для каждого куба, группы мер или секции и, если найдено, значение **New** элемент используется для обновления  **StorageLocation** объекта во время восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
