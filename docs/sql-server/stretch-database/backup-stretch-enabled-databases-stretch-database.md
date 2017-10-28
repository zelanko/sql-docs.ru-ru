---
title: "Резервное копирование баз данных с поддержкой Stretch (база данных Stretch) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, backing up
- backups (Stretch Database)
ms.assetid: 18f0dff0-d8ce-4bee-a935-76ed6dfb3208
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 75460a6396a410f7f61623e2273465a8e138f773
ms.contentlocale: ru-ru
ms.lasthandoff: 07/29/2017

---
# <a name="backup-stretch-enabled-databases-stretch-database"></a>Резервное копирование баз данных с поддержкой Stretch (база данных Stretch)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 Резервные копии позволяют восстанавливать базы данных после различных сбоев, ошибок и аварийных ситуаций.  
  
 -   Резервные копии необходимо создавать для баз данных SQL Server с поддержкой Stretch.  
      
 -   Microsoft Azure автоматически создает резервную копию удаленных данных, переносимых базой данных Stretch из SQL Server в Azure.  

> [!TIP]
> Резервная копия — только часть комплексного решения обеспечения высокой доступности и бесперебойной работы. Дополнительные сведения о высокой доступности см. в статье [Решения высокого уровня доступности](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).
   
## <a name="back-up-your-sql-server-data"></a>Резервное копирование данных SQL Server  
  
Для резервного копирования баз данных с поддержкой растяжения можно использовать те же методы, что и для резервного копирования SQL Server. Дополнительные сведения см. в статье [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).
  
 Резервные копии базы данных SQL Server с поддержкой растяжения содержат только локальные данные и данные, доступные для переноса на момент резервного копирования. (Доступные для переноса данные — это данные, которые еще не перемещены, но будут перемещены в Azure с учетом параметров таблиц.) Такое резервное копирование называется **поверхностным** и не включает данные, уже перенесенные в Azure.  
  
## <a name="back-up-your-remote-azure-data"></a>Резервное копирование удаленных данных Azure   
  
Microsoft Azure автоматически создает резервную копию удаленных данных, переносимых базой данных Stretch из SQL Server в Azure.    
### <a name="azure-reduces-the-risk-of-data-loss-with-automatic-backup"></a>Azure уменьшает риск потери данных за счет автоматического создания резервных копий  
Служба баз данных Stretch SQL Server в Azure защищает удаленные базы данных, создавая автоматические моментальные снимки хранилища не реже, чем через каждые 8 часов. Каждый снимок хранится в течение 7 дней, что позволяет выбрать удобную точку восстановления.  
  
### <a name="azure-reduces-the-risk-of-data-loss-with-geo-redundancy"></a>Azure уменьшает риск потери данных за счет геоизбыточности  
Резервные копии баз данных Azure хранятся в геоизбыточном хранилище Azure (RA-GRS), а значит, по умолчанию геоизбыточны. Геоизбыточное хранилище реплицирует данные в дополнительный регион, который находится в сотнях километров от основного региона. И в основном, и в дополнительном регионах данные реплицируются по три раза в отдельные домены сбоя и обновления. Это гарантирует, что данные будут сохранены даже в случае региональной аварии или сбоя, в результате которых один из регионов Azure станет недоступен.

### <a name="stretchRPO"></a>Базы данных Stretch снижает риск потери данных Azure за счет временного хранения перенесенных строк
Выполнив перенос доступных строк с SQL Server в Azure, база данных Stretch сохраняет эти строки в промежуточной таблице не меньше чем на 8 часов. При восстановлении резервной копии базы данных Azure база данных Stretch использует строки, сохраненные в промежуточной таблице, для согласования баз данных SQL Server и Azure.

После восстановления резервной копии данных Azure необходимо выполнить хранимую процедуру [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы восстановить подключение базы данных SQL Server с поддержкой Stretch к удаленной базе данных Azure. При запуске процедуры **sys.sp_rda_reauthorize_db**база данных Stretch автоматически согласовывает базы данных SQL Server и Azure.

Чтобы увеличить длительность хранения перенесенных данных в промежуточной таблице базы данных Stretch, выполните хранимую процедуру [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) , указав число часов больше 8. Определить объем данных для хранения помогут следующие факторы:
-   Частота автоматического резервного копирования Azure (не реже, чем раз в 8 часов).
-   Время, необходимое для распознавания возникшей проблемы и принятия решения о восстановлении базы данных из резервной копии.
-   Длительность операции восстановления Azure.

> [!NOTE]
> С увеличением объема данных, временно сохраняемых базой данных Stretch в промежуточной таблице, увеличивается объем необходимого места в SQL Server.

Чтобы проверить длительность хранения данных, хранящихся в промежуточной таблице базы данных Stretch в текущий момент, выполните хранимую процедуру [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).

## <a name="see-also"></a>См. также:  
[Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
 [Управление базой данных Stretch и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
   
  
  

