---
title: Мониторинг переноса данных и устранение неполадок
ms.date: 06/14/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, monitoring
- monitoring Stretch Database
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: d204c7acfbd8598a7cbb66a41dcf89915fc711ef
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "73843781"
---
# <a name="monitor-and-troubleshoot-data-migration-stretch-database"></a>Мониторинг переноса данных и устранение неполадок при этой операции (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Чтобы отслеживать перенос данных в мониторе Stretch Database, следует выбрать в SQL Server Management Studio **Задачи | Stretch | Монитор** для базы данных.  
  
## <a name="check-the-status-of-data-migration-in-the-stretch-database-monitor"></a>Проверка состояния переноса данных в мониторе Stretch Database  
 Чтобы открыть монитор Stretch Database и отслеживать перенос данных, в SQL Server Management Studio выберите **Задачи | Stretch | Монитор** для базы данных.  
  
-   В верхней области монитора отображаются общие сведения о базе данных SQL Server с поддержкой Stretch и удаленной базе данных Azure.  
  
-   В нижней области монитора отображается состояние переноса данных для каждой таблицы с поддержкой Stretch в базе данных.  
  
 ![Мониторинг базы данных Stretch Database](../../sql-server/stretch-database/media/stretch-monitor.PNG "Мониторинг базы данных Stretch Database")  
  
##  <a name="check-the-status-of-data-migration-in-a-dynamic-management-view"></a><a name="Migration"></a> Проверка состояния переноса данных в динамическое административное представление  
 Откройте динамическое представление управления **sys.dm_db_rda_migration_status** , чтобы увидеть, сколько разделов и строк данных было перенесено. Дополнительные сведения см. в разделе [sys.dm_db_rda_migration_status (Transact-SQL)](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
##  <a name="troubleshoot-data-migration"></a><a name="Firewall"></a> Устранение неполадок переноса данных  
 **Строки из таблицы с поддержкой Stretch не переносятся в Azure. В чем может быть проблема?**  
 Есть некоторые проблемы, которые могут повлиять на процедуру переноса. Проверьте следующее.  
  
-   Проверьте сетевое подключение на компьютере с SQL Server.  
  
-   Убедитесь, что брандмауэр Azure не блокирует подключение SQL Server к удаленной конечной точке.  
  
-   Проверьте статус последнего пакета в динамическом представлении управления **sys.dm_db_rda_migration_status** . Если произошла ошибка, проверьте значения error_number, error_state и error_severity для пакета.  
  
    -   Дополнительные сведения об этом представлении см. в разделе [sys.dm_db_rda_migration_status (Transact-SQL)](../../relational-databases/system-dynamic-management-views/stretch-database-sys-dm-db-rda-migration-status.md).  
  
    -   Дополнительные сведения о содержимом сообщения об ошибке SQL Server см. в разделе [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md).  
  
 **Брандмауэр Azure блокирует подключения из локального сервера.**  
 Вам может потребоваться добавить правило в параметры брандмауэра для сервера Azure, чтобы позволить SQL Server взаимодействовать с удаленным сервером Azure.  
  
## <a name="see-also"></a>См. также:  
 [Управление Stretch Database и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  
  
  
