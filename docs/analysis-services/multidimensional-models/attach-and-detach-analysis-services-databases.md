---
title: "Присоединение и отсоединение баз данных служб Analysis Services | Документы Microsoft"
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
f1_keywords:
- sql13.asvs.ssmsimbi.AttachDatabase.f1
- sql13.asvs.ssms.attachdatabase.f1
- sql13.asvs.ssmsimbi.DetachDatabase.f1
- sql13.asvs.ssms.detachdatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4abef02a67a334486b123a2ed29b8119e7a29f8b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="attach-and-detach-analysis-services-databases"></a>Подключение и отключение баз данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Часто возникают ситуации при [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратор базы данных (dba) требуется некоторое время перевести базу данных в автономный режим, а затем перевести ее обратно в оперативный режим, в том же экземпляре сервера, или на другом. Такие ситуации часто обусловлены потребностями предприятия, например необходимостью переместить базу данных на другой диск для повышения производительности, освободить место для увеличения размера базы данных или при обновлении какого-либо продукта. В этих и других случаях команды **Attach** и **Detach** позволяют администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] переводить базу данных в режим "вне сети" и обратно в режим "в сети" с минимальными усилиями.  
  
## <a name="attach-and-detach-commands"></a>Команды Attach и Detach  
 Команда **Attach** позволяет перевести базу данных из режима «вне сети» в режим «в сети». База данных может быть присоединена как к исходному, так и к любому другому экземпляру сервера. При присоединении базы данных пользователь может указать для нее значение свойства **ReadWriteMode** . Команда **Detach** позволяет перевести базу данных на сервере в режим «вне сети».  
  
## <a name="attach-and-detach-usage"></a>Использование команд Attach и Detach  
 Команда **Attach** позволяет перевести в режим «в сети» существующую структуру базы данных. Если база данных присоединена в режиме **ReadWrite** , она может быть присоединена к экземпляру сервера только один раз. Если же база данных присоединена в режиме **ReadOnly** , она может быть присоединена к нескольким экземплярам сервера. Это, однако, не означает, что база данных может быть присоединена к одному экземпляру сервера более одного раза. Если попытаться сделать это (даже после копирования данных в другую папку), будет выдана ошибка.  
  
> [!IMPORTANT]  
>  Если для отсоединения базы данных потребовался пароль, для ее присоединения необходим тот же пароль.  
  
 Команда **Detach** позволяет перевести в режим «вне сети» существующую структуру базы данных. При отсоединении базы данных можно указать пароль для защиты конфиденциальных метаданных.  
  
> [!IMPORTANT]  
>  Чтобы обеспечить защиту содержимого файлов данных, необходимо защитить папку, вложенные папки и файлы данных с помощью списков управления доступом.  
  
 При отсоединении базы данных сервер выполняет следующие шаги.  
  
|Отсоединение базы данных в режиме чтения и записи|Отсоединение базы данных в режиме только для чтения|  
|--------------------------------------|-------------------------------------|  
|1. Сервер выполняет запрос блокировки CommitExclusive для базы данных.<br /><br /> 2. Сервер ожидает, пока все входящие транзакции завершатся фиксацией или откатом.<br /><br /> 3. Сервер формирует все метаданные, необходимые для отключения базы данных.<br /><br /> 4. База данных помечается как удаленная.<br /><br /> 5. Сервер фиксирует транзакцию.|1. База данных помечается как удаленная.<br /><br /> 2. Сервер фиксирует транзакцию.<br /><br /> Примечание. Нельзя сменить пароль для базы данных в режиме только для чтения. Если указать пароль для присоединяемой базы данных, уже защищенной паролем, возникнет ошибка.|  
  
 Команды **Attach** и **Detach** должны выполняться в пределах одной операции. Они не могут сочетаться в одной транзакции с другими операциями. Кроме того, команды **Attach** и **Detach** являются атомарными транзакционными командами. Это означает, что только вся операция целиком может завершиться либо успешно, либо неуспешно. База данных не может остаться в незавершенном состоянии.  
  
> [!IMPORTANT]  
>  Чтобы выполнить команду **Detach** , необходимы права администратора сервера или базы данных.  
  
> [!IMPORTANT]  
>  Чтобы выполнить команду **Attach** , необходимы права администратора сервера.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Режимы ReadWriteModes базы данных](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Элемент detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Элемент Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  
