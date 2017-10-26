---
title: "Просмотр и настройка параметров соединения с удаленным сервером (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 700524e1605ef7ff871d7308ea1b4caa359081c9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a>Просмотр и настройка параметров соединения с удаленным сервером (SQL Server)
  В этом разделе описываются способы просмотра и настройки параметров подключения к удаленному серверу на уровне сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Просмотр и настройка параметров соединения с удаленным сервером с использованием**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметров соединения с удаленным сервером](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для выполнения хранимой процедуры **sp_serveroption** необходимо разрешение ALTER ANY LINKED SERVER на сервер.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a>Просмотр и настройка параметров соединения с удаленным сервером  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства SQL Server — \<***имя_сервера***>** щелкните элемент **Соединения**.  
  
3.  На странице **Соединения** просмотрите параметры **Соединения с удаленными серверами** и измените их при необходимости.  
  
4.  Повторите шаги 1-3 на другом сервере данной пары серверов.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-remote-server-connection-options"></a>Просмотр параметров соединения удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере хранимая процедура [sp_helpserver](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md) используется для возврата сведений обо всех удаленных серверах.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a>Настройка параметров соединения с удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md) для настройки удаленного сервера. В следующем примере удаленный сервер настраивается в соответствии с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, для совместимости параметров сортировки с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметров соединения с удаленным сервером  
 Чтобы изменения вступили в силу, необходимо остановить и перезапустить удаленный сервер.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Удаленные серверы](../../database-engine/configure-windows/remote-servers.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)  
  
  

