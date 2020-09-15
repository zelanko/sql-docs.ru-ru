---
description: Резервное копирование баз данных с поддержкой Stretch (Stretch Database)
title: Резервное копирование баз данных с поддержкой Stretch
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
ms.custom: seo-dt-2019
ms.openlocfilehash: 38ee204a715e691654e550f849ccf0216c715edc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423128"
---
# <a name="backup-stretch-enabled-databases-stretch-database"></a>Резервное копирование баз данных с поддержкой Stretch (Stretch Database)
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


 Резервные копии позволяют восстанавливать базы данных после различных сбоев, ошибок и аварийных ситуаций.  
  
 -   Резервные копии необходимо создавать для баз данных SQL Server с поддержкой Stretch.  
      
 -   Microsoft Azure автоматически архивирует удаленные данные, которые служба Stretch Database перенесла из SQL Server в Azure.  

> [!TIP]
> Резервная копия — только часть комплексного решения обеспечения высокой доступности и бесперебойной работы. Дополнительные сведения о высокой доступности см. в статье [Решения высокого уровня доступности](../../database-engine/sql-server-business-continuity-dr.md).
   
## <a name="back-up-your-sql-server-data"></a>Резервное копирование данных SQL Server  
  
Для резервного копирования баз данных с поддержкой растяжения можно использовать те же методы, что и для резервного копирования SQL Server. Дополнительные сведения см. в статье [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).
  
 Резервные копии базы данных SQL Server с поддержкой растяжения содержат только локальные данные и данные, доступные для переноса на момент резервного копирования. (Доступные для переноса данные — это данные, которые еще не перемещены, но будут перемещены в Azure с учетом параметров таблиц.) Такое резервное копирование называется **поверхностным** и не включает данные, уже перенесенные в Azure.  
  
## <a name="back-up-your-remote-azure-data"></a>Резервное копирование удаленных данных Azure   
  
Microsoft Azure автоматически архивирует удаленные данные, которые служба Stretch Database перенесла из SQL Server в Azure.    
### <a name="azure-reduces-the-risk-of-data-loss-with-automatic-backup"></a>Azure уменьшает риск потери данных за счет автоматического создания резервных копий  
Служба SQL Server Stretch Database в Azure защищает удаленные базы данных с помощью автоматического создания моментальных снимков хранилища по крайней мере каждые 8 часов. Каждый снимок хранится в течение 7 дней, что позволяет выбрать удобную точку восстановления.  
  
### <a name="azure-reduces-the-risk-of-data-loss-with-geo-redundancy"></a>Azure уменьшает риск потери данных за счет геоизбыточности  
Резервные копии баз данных Azure хранятся в геоизбыточном хранилище Azure (RA-GRS), а значит, по умолчанию геоизбыточны. Геоизбыточное хранилище реплицирует данные в дополнительный регион, который находится в сотнях километров от основного региона. И в основном, и в дополнительном регионах данные реплицируются по три раза в отдельные домены сбоя и обновления. Это гарантирует, что данные будут сохранены даже в случае региональной аварии или сбоя, в результате которых один из регионов Azure станет недоступен.

### <a name="stretch-database-reduces-the-risk-of-data-loss-for-your-azure-data-by-retaining-migrated-rows-temporarily"></a><a name="stretchRPO"></a>Stretch Database снижает риск потери данных Azure за счет временного хранения перенесенных строк
После того, как Stretch Database перенесет пригодные строки из SQL Server в Azure, она хранит их в промежуточной таблице не менее 8 часов. В случае восстановления резервной копии базы данных Azure служба Stretch Database использует строки, сохраненные в промежуточной таблице, для согласования баз данных SQL Server и Azure.

После восстановления резервной копии данных Azure необходимо выполнить хранимую процедуру [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) , чтобы восстановить подключение базы данных SQL Server с поддержкой Stretch к удаленной базе данных Azure. При выполнении **sys.sp_rda_reauthorize_db** Stretch Database автоматически согласовывает базы данных SQL Server и Azure.

Чтобы увеличить период временного хранения в промежуточной таблице данных, перенесенных службой Stretch Database, выполните хранимую процедуру [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) и укажите число часов больше 8. Определить объем данных для хранения помогут следующие факторы:
-   Частота автоматического резервного копирования Azure (не реже, чем раз в 8 часов).
-   Время, необходимое для распознавания возникшей проблемы и принятия решения о восстановлении базы данных из резервной копии.
-   Длительность операции восстановления Azure.

> [!NOTE]
> Увеличение объема данных, которые служба Stretch Database временно хранит в промежуточной таблице, увеличивает требуемый объем пространства SQL Server.

Чтобы узнать, сколько часов данные, перенесенные службой Stretch Database, хранятся в промежуточной таблице в настоящее время, выполните хранимую процедуру [sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).

## <a name="see-also"></a>См. также:  
[Восстановление баз данных с поддержкой Stretch](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
 [Управление службой Stretch Database и устранение неполадок, связанных с ее использованием](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
   
  
  
