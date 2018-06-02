---
title: Объект элемента (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9ef2f645895e567d69d06e4e1383e0c477b6ed1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575916"
---
# <a name="object-element-xmla"></a>Элемент Object (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит ссылку на объект, которая используется родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element relationships table -->  
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
|Количество элементов|См. таблицу ниже.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[ALTER](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)|0-1: необязательный элемент, который может встречаться только один раз.|  
|Все остальные|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ALTER](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [удаление](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [блокировки](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [подписаться](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [синхронизации](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|Обязательные элементы языка ASSL. Указывается перечислением элементов ID объекта и его предков (исключая **сервера** объекта.) Например, следующая **объекта** определяет секцию:<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Примечания  
 Порядок следования идентификаторов неважен.  
  
 Для **Alter** элементов в экземпляре служб Analysis Services используется в качестве объекта по умолчанию, если **объекта** элемент не указан.  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
