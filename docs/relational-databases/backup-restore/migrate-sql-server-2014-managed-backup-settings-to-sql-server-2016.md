---
title: "Перенос параметров управляемой архивации SQL Server 2014 в SQL Server 2016 | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 902ad2ddd95a26f36ff9519e55d7af77ca7e2d8a
ms.lasthandoff: 04/11/2017

---
# <a name="migrate-sql-server-2014-managed-backup-settings-to-sql-server-2016"></a>Перенос параметров управляемой архивации SQL Server 2014 в SQL Server 2016
  В этом разделе рассматриваются вопросы миграции для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] при обновлении [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
 В [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] процедуры и принцип действия [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]изменились. В следующих разделах описаны функциональные изменения и их последствия.  
  
## <a name="overview"></a>Обзор  
 В следующей таблице описаны некоторые основные функциональные отличия [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] между [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
|Область|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**Пространство имен:**|smart_admin|managed_backup|  
|**Системные хранимые процедуры:**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**Безопасность:**|В учетных данных SQL используется учетная запись хранения Microsoft Azure и ключ доступа к хранилищу.|В учетных данных SQL используется маркер подписанного URL-адреса Microsoft Azure (SAS).|  
|**Базовое хранилище:**|Служба хранилища Microsoft Azure, использующая страничные BLOB-объекты.|Служба хранилища Microsoft Azure, использующая блочные BLOB-объекты.|  
  
## <a name="benefits"></a>Преимущества  
 У новых возможностей [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]есть несколько преимуществ.  
  
-   Меньше затраты на хранение блочных BLOB-объектов.  
  
-   Используя чередование, можно хранить резервные копии гораздо большего размера (12 ТБ вместо 1 ТБ для страничных BLOB-объектов).  
  
-   Чередование также сокращает время восстановления для больших баз данных.  
  
-   Сведения о других улучшениях [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]см. в разделе [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="considerations"></a>Замечания  
 После обновления [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]обратите внимание на следующие вопросы [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] .  
  
-   Все базы данных, для которых ранее было настроено [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , будут продолжать использовать в **системные процедуры** smart_admin [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]и базовое поведение.  
  
-   В **не поддерживаются процедуры** smart_admin [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для всех новых конфигураций [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Необходимо использовать новые процедуры и функции **managed_backup** .  
  
## <a name="see-also"></a>См. также:  
 [Управляемое резервное копирование SQL Server в Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
