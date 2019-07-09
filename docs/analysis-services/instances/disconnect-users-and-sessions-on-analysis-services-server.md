---
title: Отключение пользователей и сеансов на анализе сервера служб | Документация Майкрософт
ms.date: 07/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 696c6548dadda2412566acf7fae1e2cff2b28095
ms.sourcegitcommit: 9af07bd57b76a34d3447e9e15f8bd3b17709140a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624400"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Отключение пользователей и сеансов на сервере служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  Будучи администратором может потребоваться завершить пользовательские операции в процессе управления рабочей нагрузкой. Это производится путем отмены сеансов и соединений. Сеансы могут формироваться автоматически при запуске запроса (неявно) или именоваться в момент создания администратором (явно). Соединения представляют собой открытые каналы, по которым запускаются запросы. Как сеансы, так и соединения можно завершать, пока они активны. Например может потребоваться прекратить обработку для сеанса, если обработка занимает слишком много времени, или в том случае, если некоторые возникли сомнения ли правильности написания выполняемой команды.  
  
## <a name="ending-sessions-and-connections"></a>Завершение сеансов и соединений  
 Для управления сеансами и соединениями, используйте динамические административные представления (DMV) и XML для Аналитики:  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб Analysis Services.  
  
2.  Вставьте один из следующих запросов к динамическим административным представлениям (DMV) в окно запроса MDX, чтобы получить список всех активных в настоящее время сеансов, соединений и выполняющихся команд.  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  (Этот запрос не относится к службам Azure Analysis Services)
  
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

Отмена SessionID или SPID отменит все active команды, выполняющиеся в сеанс, соответствующий SPID/SessionID. Отмена подключения идентификации сеанса, связанный с подключением и отменить все active команды, выполняющиеся в этом сеансе. В редких случаях подключение не закрывается, если модуль не может отследить все сеансы и SPID, связанный с соединением; например когда несколько сеансов, откройте в сценарии HTTP.   
  
Дополнительные сведения о XMLA, упомянутом в данном разделе, см. в разделе [выполнить метод &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) и [элемент Cancel &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).  
  
## <a name="see-also"></a>См. также  
 [Управление соединениями и сеансами (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Элемент BeginSession (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [Элемент EndSession (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Элемент Session (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
