---
title: Объект элемента (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Object Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: 99470537-2c4a-4072-9613-940c41c12487
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e4fb7e25b9e813487b612bbd6269c2f080d85f5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178754"
---
# <a name="object-element-xmla"></a>Элемент Object (XML для аналитики)
  Содержит ссылку на объект, которая используется родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Alter> <!-- or any of the parent elements in the Element Relationships table -->  
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
|Количество элементов|Предок или родитель: [Alter](../xml-elements-commands/create-element-xmla.md) &#124; 0-1: необязательный элемент, который может появляться только один раз.<br /><br /> Предок или родитель: все остальные &#124; 1-1: обязательный элемент, который встречается только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ALTER](../xml-elements-commands/alter-element-xmla.md), [резервного копирования](../xml-elements-commands/backup-element-xmla.md), [ClearCache](../xml-elements-commands/clearcache-element-xmla.md), [удалить](../xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md), [блокировки](../xml-elements-commands/lock-element-xmla.md), [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md), [процесс](../xml-elements-commands/process-element-xmla.md), [подписаться](../xml-elements-commands/subscribe-element-xmla.md), [синхронизации](../xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|Обязательные элементы языка ASSL. Указывается перечислением элементов ID объекта и его предков (исключая объект `Server`). Например, следующий элемент `Object` определяет секцию.<br /><br /> `<Object>`<br /><br /> `<DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>`<br /><br /> `<CubeID>Adventure Works</CubeID>`<br /><br /> `<MeasureGroupID>Internet Sales</MeasureGroupID>`<br /><br /> `<PartitionID>Inernet_Sales_2001</PartitionID>`<br /><br /> `</Object>`|  
  
## <a name="remarks"></a>Примечания  
 Порядок следования идентификаторов неважен.  
  
 Для `Alter` элементов, экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используется в качестве объекта по умолчанию, если `Object` элемент не указан.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
