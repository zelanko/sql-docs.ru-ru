---
title: "Элемент (XMLA) Subscribe | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Subscribe Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords: Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 47425fd75c42d70ad98172eee2070bdcb9b2db45
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="subscribe-element-xmla"></a>Элемент Subscribe (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Подписывается на трассировку и возвращает набор строк, содержащий события трассировки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 **Subscribe** команда подписывается на трассировку и возвращает набор строк из указанной трассировки на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если в элементе **Object** указать объект, отличный от трассировки, возникает ошибка.  
  
 Если **объекта** элемент не указан, трассировка сеанса определяется и выполняется подписка на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Трассировка сеанса возвращает фиксированный набор событий трассировки из текущего сеанса.  
  
 Возвращенный этой командой поток строк завершается, если клиентское приложение закрывает соединение [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, или если сеанс, в котором **Subscribe** выполняется команда завершается.  
  
## <a name="see-also"></a>См. также:  
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
