---
title: Заблокировать элемент (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Lock Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98e5087dc10ae495dec711c35fa807cb9fd68e02
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lock-element-xmla"></a>Элемент Lock (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Блокирует указанный объект в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
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
|Дочерние элементы|[Идентификатор](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [режим](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Команда **Lock** блокирует объект для совместного или монопольного использования в контексте текущей активной транзакции. Явно выполнять команду **Lock** могут только администраторы базы данных или администраторы сервера. Блокировка объекта не позволяет фиксировать транзакции, пока она не будет снята. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают два типа блокировок: совмещаемые и монопольные. Дополнительные сведения о поддерживаемых типах блокировки [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [режим элемент &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] позволяют блокировать только базы данных. **Объекта** элемент должен содержать ссылку на объект [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных. Если элемент **Object** не указан или если элемент **Object** ссылается на объект, отличающийся от базы данных, возникает ошибка.  
  
 Другие команды неявно выполняют **блокировки** на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных. Любая операция по чтению данных или метаданных из базы данных, например любой метод **Discover** или метод **Execute** , запускающий команду **Statement** , неявно устанавливает совмещаемую блокировку для базы данных. Любая транзакция, фиксирующая изменения в данных или метаданных объекта в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных, например **Execute** метод, выполняемый **Alter** неявным образом устанавливает монопольную блокировку на База данных.  
  
 Все блокировки удерживаются в контексте текущей транзакции. После фиксации или отката текущей транзакции все блокировки, определенные в рамках транзакции, автоматически снимаются.  
  
## <a name="see-also"></a>См. также:  
 [Разблокировать элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
