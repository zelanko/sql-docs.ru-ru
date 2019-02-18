---
title: Резервное копирование баз данных с поддержкой Stretch (Stretch Database) | Документация Майкрософт
ms.date: 06/14/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, disabling
- disabling Stretch Database
ms.assetid: 18f0dff0-d8ce-4bee-a935-76ed6dfb3208
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7e7fb7bc85c3dbe56ed0ba4e694c04e0abea66c1
ms.sourcegitcommit: ec1f01b4bb54621de62ee488decf9511d651d700
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56240718"
---
# <a name="backup-stretch-enabled-databases-stretch-database"></a>Резервное копирование баз данных с поддержкой Stretch (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


 Резервные копии позволяют восстанавливать базы данных после различных сбоев, ошибок и аварийных ситуаций.  
  
 -   Резервные копии необходимо создавать для баз данных SQL Server с поддержкой Stretch.  
      
 -   Microsoft Azure автоматически создает резервную копию удаленных данных, переносимых Stretch Database из SQL Server в Azure.  

> [!TIP]
> Резервная копия — только часть комплексного решения обеспечения высокой доступности и бесперебойной работы. Дополнительные сведения о высокой доступности см. в статье [Решения высокого уровня доступности](../../database-engine/sql-server-business-continuity-dr.md).
   
## <a name="back-up-your-sql-server-data"></a>Резервное копирование данных SQL Server  
  
Для резервного копирования баз данных с поддержкой растяжения можно использовать те же методы, что и для резервного копирования SQL Server. Дополнительные сведения см. в статье [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).
  
 Резервные копии базы данных SQL Server с поддержкой растяжения содержат только локальные данные и данные, доступные для переноса на момент резервного копирования. (Доступные для переноса данные — это данные, которые еще не перемещены, но будут перемещены в Azure с учетом параметров таблиц.) Такое резервное копирование называется **поверхностным** и не включает данные, уже перенесенные в Azure.  
  
## <a name="back-up-your-remote-azure-data"></a>Резервное копирование удаленных данных Azure   
  
Microsoft Azure автоматически создает резервную копию удаленных данных, переносимых Stretch Database из SQL Server в Azure.    
### <a name="azure-reduces-the-risk-of-data-loss-with-automatic-backup"></a>Azure уменьшает риск потери данных за счет автоматического создания резервных копий  
Служба SQL Server Stretch Database в Azure защищает удаленные базы данных, создавая автоматические моментальные снимки хранилища не реже, чем через каждые 8 часов. Каждый снимок хранится в течение 7 дней, что позволяет выбрать удобную точку восстановления.  
  
### <a name="azure-reduces-the-risk-of-data-loss-with-geo-redundancy"></a>Azure уменьшает риск потери данных за счет геоизбыточности  
Резервные копии баз данных Azure хранятся в геоизбыточном хранилище Azure (RA-GRS), а значит, по умолчанию геоизбыточны. Геоизбыточное хранилище реплицирует данные в дополнительный регион, который находится в сотнях километров от основного региона. И в основном, и в дополнительном регионах данные реплицируются по три раза в отдельные домены сбоя и обновления. Это гарантирует, что данные будут сохранены даже в случае региональной аварии или сбоя, в результате которых один из регионов Azure станет недоступен.

### <a name="stretchRPO"></a>Stretch Database снижает риск потери данных Azure за счет временного хранения перенесенных строк
Выполнив перенос доступных строк с SQL Server в Azure, Stretch Database сохраняет эти строки в промежуточной таблице не меньше чем на 8 часов. При восстановлении резервной копии базы данных Azure база данных Stretch Database использует строки, сохраненные в промежуточной таблице, для согласования баз данных SQL Server и Azure.

После восстановления резервной копии данных Azure необходимо выполнить хранимую процедуру [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы восстановить подключение базы данных SQL Server с поддержкой Stretch к удаленной базе данных Azure. При запуске процедуры **sys.sp_rda_reauthorize_db**Stretch Database автоматически согласовывает базы данных SQL Server и Azure.

Чтобы увеличить длительность хранения перенесенных данных в промежуточной таблице Stretch Database, выполните хранимую процедуру [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md), указав число часов больше 8. Определить объем данных для хранения помогут следующие факторы:
-   Частота автоматического резервного копирования Azure (не реже, чем раз в 8 часов).
-   Время, необходимое для распознавания возникшей проблемы и принятия решения о восстановлении базы данных из резервной копии.
-   Длительность операции восстановления Azure.

> [!NOTE]
> С увеличением объема данных, временно сохраняемых базой данных Stretch Database в промежуточной таблице, увеличивается объем необходимого места в SQL Server.

Чтобы проверить длительность хранения данных, хранящихся в промежуточной таблице Stretch Database в текущий момент, выполните хранимую процедуру [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).

## <a name="see-also"></a>См. также:  
[Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
 [Управление Stretch Database и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
   
  
  
