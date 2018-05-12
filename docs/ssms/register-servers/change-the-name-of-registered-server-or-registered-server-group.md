---
title: Изменение имени зарегистрированного сервера или зарегистрированной группы серверов | Документы Майкрософт
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-registration
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying registered server or server group names
- server groups [SQL Server]
- Registered Servers [SQL Server], names
- renaming registered server or server group
- names [SQL Server], registered server or server group
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9a1455eadba4fe4d8ec2072df8f5f5fc11f29ef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Изменение имени зарегистрированного сервера или зарегистрированной группы серверов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
  
