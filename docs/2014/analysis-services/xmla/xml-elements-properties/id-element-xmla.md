---
title: Элемент ID (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords:
- ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86a24d14a0c9e198c879e4dce092f430a4755871
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110134"
---
# <a name="id-element-xmla"></a>Элемент ID (XML для аналитики)
  Определяет блокировку, в котором должен выполняться родительский [блокировки](../xml-elements-commands/lock-element-xmla.md) или [Unlock](../xml-elements-commands/unlock-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
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
|Родительские элементы|[Блокировка](../xml-elements-commands/lock-element-xmla.md), [разблокировки](../xml-elements-commands/unlock-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `ID` содержит глобальный уникальный идентификатор (GUID), использующийся для идентификации блокировки.  
  
## <a name="see-also"></a>См. также  
 [Объект элемента &#40;XML для Аналитики&#41;](object-element-xmla.md)   
 [Элемент Mode &#40;XML для Аналитики&#41;](mode-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
