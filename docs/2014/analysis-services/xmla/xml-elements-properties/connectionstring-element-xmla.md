---
title: Элемент ConnectionString (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ConnectionString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b4f186e7beebedd11a9100d1091fc38acaa9dc0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061494"
---
# <a name="connectionstring-element-xmla"></a>Элемент ConnectionString (XML для аналитики)
  Содержит строку подключения, используемой родительским [расположение](location-element-xmla.md) или [источника](source-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов - предок или родитель|Количество элементов|  
|[Расположение](location-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|[Source](source-element-xmla.md)|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Расположение](location-element-xmla.md), [источника](source-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `Location` элемент `ConnectionString` содержит строку соединения, используемую командой `Restore` или `Synchronize`, чтобы обновить локальный источник данных или установить соединение с удаленным экземпляром.  
  
 Для элементов `Source` элемент `ConnectionString` содержит строку соединения, используемую командой `Synchronize`, чтобы установить соединение с исходным экземпляром.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент RESTORE &#40;XML для Аналитики&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
