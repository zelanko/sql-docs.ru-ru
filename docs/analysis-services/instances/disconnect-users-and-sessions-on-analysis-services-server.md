---
title: "Отключение пользователей и сеансов на анализе сервера служб | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9878a5d6577cdeb1e7c5f29b40378af3f4733074
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Отключение пользователей и сеансов на сервере служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Администратор [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может понадобиться завершить пользовательские операции при управлении рабочей нагрузкой. Это производится путем отмены сеансов и соединений. Сеансы могут формироваться автоматически при запуске запроса (неявно) или именоваться в момент создания администратором (явно). Соединения представляют собой открытые каналы, по которым запускаются запросы. Как сеансы, так и соединения можно завершать, пока они активны. Например, администратору может потребоваться прекратить обработку для сеанса, если эта обработка продолжается слишком долго или возникли сомнения в правильности написания выполняемой команды.  
  
## <a name="ending-sessions-and-connections"></a>Завершение сеансов и соединений  
 Для управления сеансами и соединениями можно использовать динамические административные представления (DMV) и XML для аналитики (XMLA):  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб Analysis Services.  
  
2.  Вставьте один из следующих запросов к динамическим административным представлениям (DMV) в окно запроса MDX, чтобы получить список всех активных в настоящее время сеансов, соединений и выполняющихся команд.  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  Нажмите клавишу F5, чтобы выполнить запрос.  
  
     Запрос DMV возвращает информацию о сеансе и соединении в виде табличного результирующего набора, что облегчает ее чтение и копирование.  
  
 Не закрывайте окно запроса. На следующем этапе вам может понадобиться вернуться на эту страницу, чтобы скопировать SPID сеанса, который требуется отключить.  
  
 Чтобы завершить сеанс, откройте второе окно запроса XML для аналитики (XMLA).  
  
1.  Вставьте следующий синтаксис в окне запроса MDX, заменив заполнители ConnectionID, SessionID или SPID на допустимые значения, скопированные из предыдущего этапа.  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Нажмите клавишу F5, чтобы выполнить команду отмены.  
  
 При закрытии соединения отменяются все сеансы и SPID, закрывая сеанс узла.  
  
 Завершение сеанса останавливает все команды (SPID), которые выполняются в рамках этого сеанса.  
  
 Завершение SPID отменяет определенную оценку.  
  
 В редких случаях [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не закроет сеанс, если не сможет отследить все сеансы и SPID, связанные с соединением (например, когда несколько сеансов открыто в сценарии HTTP).  
  
 Дополнительную информацию о XMLA, упомянутом в данном разделе, см. в разделах [Метод Execute (XMLA)](../../analysis-services/xmla/xml-elements-methods-execute.md) и [Элемент Cancel (XMLA)](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление соединениями и сеансами (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Элемент BeginSession &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Элемент EndSession &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Элемент Session &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)  
  
  
