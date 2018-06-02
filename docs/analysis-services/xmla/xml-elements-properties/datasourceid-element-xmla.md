---
title: Элемент DataSourceID (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 883fa5df355874516ffd6f0cac01ff50d727d737
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573766"
---
# <a name="datasourceid-element-xmla"></a>Элемент DataSourceID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет источник данных, используемый [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) во время выполнения [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
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
|Родительские элементы|[Расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **DataSourceID** элемент содержит имя источника данных на экземпляре источника, который идентифицирует удаленный экземпляр, на котором находится сведений удаленной секции для резервного копирования, восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Элемент ConnectionString &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Элемент DataSourceType &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
