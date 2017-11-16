---
title: "Присоединение и отсоединение баз данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
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
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f4c193def48b92245c1e2f2955262d3fb0850957
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="attach-and-detach-analysis-services-databases"></a>Подключение и отключение баз данных служб Analysis Services
  Часто администратору базы данных (dba) служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо на некоторое время перевести базу данных в режим "вне сети", а затем перевести ее в режим "в сети" на том же или на другом экземпляре сервера. Такие ситуации часто обусловлены потребностями предприятия, например необходимостью переместить базу данных на другой диск для повышения производительности, освободить место для увеличения размера базы данных или при обновлении какого-либо продукта. В этих и других случаях команды **Attach** и **Detach** позволяют администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] переводить базу данных в режим "вне сети" и обратно в режим "в сети" с минимальными усилиями.  
  
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
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Режимы ReadWriteModes базы данных](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Элемент detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Элемент Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  

