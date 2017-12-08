---
title: "Элемент (XMLA) Subscribe | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: 324239ae113bc5f1323de718462a904b15fabc11
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="subscribe-element-xmla"></a>Элемент Subscribe (XML для аналитики)
  Подписывается на трассировку и возвращает набор строк, содержащий события трассировки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Subscribe** команда подписывается на трассировку и возвращает набор строк из указанной трассировки на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если в элементе **Object** указать объект, отличный от трассировки, возникает ошибка.  
  
 Если **объекта** элемент не указан, трассировка сеанса определяется и выполняется подписка на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Трассировка сеанса возвращает фиксированный набор событий трассировки из текущего сеанса.  
  
 Возвращенный этой командой поток строк завершается, если клиентское приложение закрывает соединение [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, или если сеанс, в котором **Subscribe** выполняется команда завершается.  
  
## <a name="see-also"></a>См. также:  
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
