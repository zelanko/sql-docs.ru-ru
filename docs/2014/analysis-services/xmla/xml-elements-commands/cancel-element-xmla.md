---
title: Отмена элемент (XMLA) | Документы Microsoft
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
- Cancel Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords:
- Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: cd0fdd50a1dcddb51d167ab76cd5408b631bb3ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190529"
---
# <a name="cancel-element-xmla"></a>Элемент Cancel (XML для аналитики)
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[CancelAssociated](../xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../xml-elements-properties/id-element-xmla.md), [SessionID](../xml-elements-properties/sessionid-element-xmla.md), [SPID](../xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `Cancel` отменяет текущие команды в контексте сеанса. Если клиентское приложение не запросило сеанс, команду нельзя отменить.  
  
 Если команда `Cancel` выполняется во время выполнения команды `Batch`, отменяется вся команда `Batch`. Если команда `Batch` входила в состав транзакции, выполняется откат всех команд, содержавшихся в `Batch`. Если команда `Batch` не входила в состав транзакции, выполняется откат только тех команд, которые выполнялись в команде `Batch` во время запуска команды `Cancel`. Откат завершенных команд, входящих с состав транзакционной команды `Batch`, не выполняется.  
  
 Как правило, команда `Cancel` используется для отмены команд в активном сеансе. В этом случае для команды `Cancel` не требуется указывать ни один из дочерних элементов. Команда `Cancel` может также использоваться администраторами для отмены команд, выполняющихся в других соединениях или сеансах, не относящихся к текущему активному сеансу. Члены роли, имеющие разрешения администратора для конкретной базы данных, могут отменять команды для соединений и сеансов, применимых к этой базе данных, в то время как администраторы сервера могут отменять команды для соединений и сеансов конкретного экземпляра служб Analysis Services.  
  
 Чтобы получить сведения о текущих соединениях и сеансах для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], можно выполнить метод `Discover`, запросив, соответственно, наборы строк схемы DISCOVER_CONNECTIONS и DISCOVER_SESSIONS. Члены роли, имеющие разрешения администратора для конкретной базы данных, могут возвращать сеансы только для этой базы данных, указав ее в столбце ограничений SESSION_CURRENT_DATABASE для наборов строк схемы DISCOVER_SESSIONS. Дополнительные сведения о `Discover` метода, в разделе [метод обнаружения &#40;XMLA&#41;](../xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Batch &#40;XML для Аналитики&#41;](batch-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  