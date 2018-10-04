---
title: Элемент RequestType (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RequestType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RequestType
- urn:schemas-microsoft-com:xml-analysis#RequestType
- microsoft.xml.analysis.requesttype
helpviewer_keywords:
- RequestType element
ms.assetid: 54270a57-e327-4233-b4b2-d85b44652ac5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 322b212853f94a1e1e5b1b48534dee649632d164
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105314"
---
# <a name="requesttype-element-xmla"></a>Элемент RequestType (XML для аналитики)
  Определяет тип метаданных, возвращенный [Discover](../xml-elements-methods-discover.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Обнаружение](../xml-elements-methods-discover.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `RequestType` определяет набор строк схемы, из которого метод `Discover` возвращает данные. Это перечисление ограничивается именами наборов строк схемы, поддерживаемых службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Дополнительные сведения о наборах строк схемы см. в разделе [наборы строк схемы служб Analysis](../../schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  В элементе `RequestType` перечисляются только имена набора строк схемы. Использование идентификатора GUID набора строк схемы приводит к ошибке.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
