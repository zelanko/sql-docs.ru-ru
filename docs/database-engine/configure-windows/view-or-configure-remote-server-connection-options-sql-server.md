---
title: Просмотр и настройка параметров соединения с удаленным сервером (SQL Server) | Документы Майкрософт
description: Узнайте, как просматривать и настраивать параметры подключения к удаленному серверу на уровне сервера. Для этого можно использовать SQL Server Management Studio или Transact-SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ec50e6ae39798add5a564dbeb8a971e879c18c27
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680716"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a>Просмотр и настройка параметров соединения с удаленным сервером (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описываются способы просмотра и настройки параметров подключения к удаленному серверу на уровне сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр и настройка параметров соединения с удаленным сервером с использованием**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметров соединения с удаленным сервером](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения хранимой процедуры **sp_serveroption** необходимо разрешение ALTER ANY LINKED SERVER на сервер.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a>Просмотр и настройка параметров соединения с удаленным сервером  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства SQL Server — \<**_server_name_**>** щелкните **Соединения**.  
  
3.  На странице **Соединения** просмотрите параметры **Соединения с удаленными серверами** и измените их при необходимости.  
  
4.  Повторите шаги 1-3 на другом сервере данной пары серверов.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-remote-server-connection-options"></a>Просмотр параметров соединения удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере хранимая процедура [sp_helpserver](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md) используется для возврата сведений обо всех удаленных серверах.  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a>Настройка параметров соединения с удаленным сервером  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md) для настройки удаленного сервера. В следующем примере удаленный сервер настраивается в соответствии с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, для совместимости параметров сортировки с локальным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметров соединения с удаленным сервером  
 Чтобы изменения вступили в силу, необходимо остановить и перезапустить удаленный сервер.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Удаленные серверы](../../database-engine/configure-windows/remote-servers.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)  
  
  
