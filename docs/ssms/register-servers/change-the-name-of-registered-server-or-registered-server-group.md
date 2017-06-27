---
title: "Изменение имени зарегистрированного сервера или зарегистрированной группы серверов | Документы Майкрософт"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying registered server or server group names
- server groups [SQL Server]
- Registered Servers [SQL Server], names
- renaming registered server or server group
- names [SQL Server], registered server or server group
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: b99eea0ee5988ce791948c2fa7340271b74e7ec4
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Изменение имени зарегистрированного сервера или зарегистрированной группы серверов
  В этом разделе описывается изменение имени зарегистрированного сервера или группы серверов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Это имя может быть изменено в любое время. Изменение имени сервера для зарегистрированных серверов изменяет только отображение имени. Чтобы подключиться к другому серверу, необходимо изменить свойства соединения зарегистрированного сервера.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
В меню перейдите к **Вид\\Зарегистрированные серверы**открыть панель **Зарегистрированные серверы**.  
#### <a name="to-change-the-name-of-a-server"></a>Изменение имени сервера  
  
1.  В списке **Зарегистрированные серверы**разверните узел **Ядро СУБД** и затем узел **Группы локальных серверов**.  

2.  Щелкните правой кнопкой мыши сервер и выберите **Свойства** , чтобы открыть диалоговое окно **Изменение данных регистрации серверов** .
  
3.  В поле **Имя зарегистрированного сервера** введите новое имя для регистрации сервера и нажмите кнопку **Сохранить**.  
  
#### <a name="to-change-the-name-of-a-server-group"></a>Изменение имени группы серверов  
  
1.  В списке **Зарегистрированные серверы**разверните узел **Ядро СУБД** и затем узел **Группы локальных серверов**.  

2.  Щелкните правой кнопкой мыши группу серверов и выберите **Свойства** , чтобы открыть диалоговое окно **Изменение свойств группы серверов** . 
  
3.  В поле **Имя группы** введите новое имя для группы серверов и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Изменение регистрационных данных сервера (среда SQL Server Management Studio)](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)  
  
  

