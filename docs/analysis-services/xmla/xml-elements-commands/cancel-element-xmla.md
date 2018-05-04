---
title: Отмена элемент (XMLA) | Документы Microsoft
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
- Cancel Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords:
- Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a7d33e58fde8a1141004b9161b69b1f813112db5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cancel-element-xmla"></a>Элемент Cancel (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Отменяет текущую команду [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Cancel>  
      <ConnectionID>...</ConnectionID>  
      <SessionID>...</SessionID>  
      <SPID>...</SPID>  
      <CancelAssociated>...</CancelAssociated>  
   </Cancel>  
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
|Дочерние элементы|[CancelAssociated](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md), [SessionID](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md), [SPID](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Команда **Cancel** отменяет текущие команды в контексте сеанса. Если клиентское приложение не запросило сеанс, команду нельзя отменить.  
  
 Если команда **Cancel** выполняется во время выполнения команды **Batch** , отменяется вся команда **Batch** . Если команда **Batch** входила в состав транзакции, выполняется откат всех команд, содержавшихся в **Batch** . Если команда **Batch** не входила в состав транзакции, выполняется откат только тех команд, которые выполнялись в команде **Batch** во время запуска команды **Cancel** . Откат завершенных команд, входящих с состав транзакционной команды **Batch** , не выполняется.  
  
 Как правило, команда **Cancel** используется для отмены команд в активном сеансе. В этом случае для команды **Cancel** не требуется указывать ни один из дочерних элементов. Команда **Cancel** может также использоваться администраторами для отмены команд, выполняющихся в других соединениях или сеансах, не относящихся к текущему активному сеансу. Члены роли, имеющие разрешения администратора для конкретной базы данных, могут отменять команды для соединений и сеансов, применимых к этой базе данных, в то время как администраторы сервера могут отменять команды для соединений и сеансов конкретного экземпляра служб Analysis Services.  
  
 Для получения сведений о текущих соединениях и сеансах для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, **Discover** метод может выполняться для запроса, соответственно, наборы строк схемы DISCOVER_CONNECTIONS и DISCOVER_SESSIONS. Члены роли, имеющие разрешения администратора для конкретной базы данных, могут возвращать сеансы только для этой базы данных, указав ее в столбце ограничений SESSION_CURRENT_DATABASE для наборов строк схемы DISCOVER_SESSIONS. Дополнительные сведения о **Discover** метода, в разделе [метод обнаружения &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Batch & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
