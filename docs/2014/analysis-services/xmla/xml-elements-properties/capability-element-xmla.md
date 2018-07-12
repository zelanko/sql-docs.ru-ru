---
title: Элемент capability (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Capability Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Capability
- http://schemas.microsoft.com/analysisservices/2003/engine#Capability
- microsoft.xml.analysis.capability
helpviewer_keywords:
- Capability element
ms.assetid: 544a733e-77fc-48a0-8f92-9cd1fdbcf824
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5b14b43b41f74c05d433c599b18486c5737b27c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201894"
---
# <a name="capability-element-xmla"></a>Элемент Capability (XML для аналитики)
  Указывает на поддержку возможностей протокола в родительском объекте [ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md) элемент заголовка.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ProtocolCapabilities](../xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `Capability` Элемент указывает, что определенные возможности, например двоичные операции или сжатие, поддерживаются либо приложением, которое включено `ProtocolCapabilities` элемент заголовка в заголовке SOAP SOAP-запроса или экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , включены `ProtocolCapabilities` элемент заголовка в заголовке SOAP SOAP-ответа. Значением элемента `Capability` является имя поддерживаемой возможности.  
  
 В следующей таблице перечислены возможности, поддерживаемые службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Имя возможности|Описание|  
|---------------------|-----------------|  
|sx|Поддержка двоичного XML|  
|xpress|Поддержка сжатия|  
  
## <a name="see-also"></a>См. также  
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
