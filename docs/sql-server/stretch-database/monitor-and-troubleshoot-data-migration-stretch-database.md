---
title: "Мониторинг переноса данных и устранение неполадок при этой операции (база данных Stretch) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "база данных Stretch, мониторинг"
  - "мониторинг базы данных Stretch"
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Мониторинг переноса данных и устранение неполадок при этой операции (база данных Stretch)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Чтобы отслеживать перенос данных в мониторе базы данных Stretch, следует выбрать в SQL Server Management Studio **Задачи | Stretch | Монитор** для базы данных.  
  
## Проверка состояния переноса данных в мониторе базы данных Stretch  
 Чтобы открыть монитор базы данных Stretch и отслеживать перенос данных, в SQL Server Management Studio выберите **Задачи | Stretch | Монитор** для базы данных.  
  
-   В верхней области монитора отображаются общие сведения о базе данных SQL Server с поддержкой Stretch и удаленной базе данных Azure.  
  
-   В нижней области монитора отображается состояние переноса данных для каждой таблицы с поддержкой Stretch в базе данных.  
  
 ![Stretch Database Monitor](../../sql-server/stretch-database/media/stretch-monitor.PNG "Stretch Database Monitor")  
  
##  <a name="Migration"></a> Проверка состояния переноса данных в динамическое административное представление  
 Откройте динамическое представление управления **sys.dm_db_rda_migration_status**, чтобы увидеть, сколько разделов и строк данных было перенесено. Дополнительные сведения см. в разделе [sys.dm_db_rda_migration_status (Transact-SQL)](../Topic/sys.dm_db_rda_migration_status%20\(Transact-SQL\).md).  
  
##  <a name="Firewall"></a> Устранение неполадок переноса данных  
 **Строки из таблицы с поддержкой Stretch не переносятся в Azure. В чем заключается проблема?**  
 Есть некоторые проблемы, которые могут повлиять на процедуру переноса. Проверьте следующее.  
  
-   Проверьте сетевое подключение на компьютере с SQL Server.  
  
-   Убедитесь, что брандмауэр Azure не блокирует подключение SQL Server к удаленной конечной точке.  
  
-   Проверьте статус последнего пакета в динамическом представлении управления **sys.dm_db_rda_migration_status**. Если произошла ошибка, проверьте значения error_number, error_state и error_severity для пакета.  
  
    -   Дополнительные сведения об этом представлении см. в разделе [sys.dm_db_rda_migration_status (Transact-SQL)](../Topic/sys.dm_db_rda_migration_status%20\(Transact-SQL\).md).  
  
    -   Дополнительные сведения о содержимом сообщения об ошибке SQL Server см. в разделе [sys.messages (Transact-SQL)](../Topic/sys.messages%20\(Transact-SQL\).md).  
  
 **Брандмауэр Azure блокирует подключения из локального сервера.**  
 Вам может потребоваться добавить правило в параметры брандмауэра для сервера Azure, чтобы позволить SQL Server взаимодействовать с удаленным сервером Azure.  
  
## См. также:  
 [Управление базой данных Stretch и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  