---
title: 'Резервное копирование и восстановление: системные базы данных'
description: SQL Server поддерживает системные базы данных, которые необходимы для работы экземпляра сервера. После каждого значительного обновления необходимо обязательно создавать резервные копии ряда системных баз данных.
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server], backing up and restoring
- restoring system databases [SQL Server]
- backing up [SQL Server], system databases
- database backups [SQL Server], system databases
- servers [SQL Server], backup
ms.assetid: aef0c4fa-ba67-413d-9359-1a67682fdaab
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d16e3159f3881df1a904e9d3a6c39bc04667ce9d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826505"
---
# <a name="backuprestoresystemdatabases-sql-server"></a>Резервное копирование и восстановление: системные базы данных (SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает набор баз данных системного уровня, которые называются*системными базами данных*и жизненно важны для работы экземпляра сервера. После каждого значительного обновления необходимо обязательно создавать резервные копии ряда системных баз данных: **msdb**, **master**и **model**. Если какая-нибудь из баз данных на экземпляре сервера использует репликацию, то необходимо также создавать резервную копию системной базы данных **distribution** . Резервные копии системных баз данных позволят восстановить систему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в случае сбоя, например отказа жесткого диска.  
  
 В следующей таблице перечислены все системные базы данных.  
  
|Системная база данных|Описание|Необходимость создавать резервные копии|Модель восстановления|Комментарии|  
|---------------------|-----------------|---------------------------|--------------------|--------------|  
|[master](../../relational-databases/databases/master-database.md)|База данных, в которой хранятся все системные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Да|Простая|Создавайте резервные копии базы данных **master** с такой частотой, которая необходима для адекватной защиты данных. Рекомендуем составить расписание регулярного резервного копирования, которое можно дополнить созданием резервных копий после значительных обновлений.|  
|[model](../../relational-databases/databases/model-database.md)|Шаблон для всех баз данных, создаваемых на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Да|Настраиваемая пользователем (0-9)|Резервные копии базы данных **model** создаются только в том случае, если они необходимы для предприятия (например сразу же после настройки параметров базы данных).<br /><br /> **Рекомендация.** Рекомендуется по мере необходимости создавать только полные резервные копии базы данных **model**. Поскольку база данных **model** невелика и редко изменяется, создавать резервную копию журнала не обязательно.|  
|[msdb](../../relational-databases/databases/msdb-database.md)|База данных, используемая агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для планирования предупреждений и заданий и для записи операторов. База данных**msdb** также содержит такие таблицы журнала, как таблицы резервных копий и журнала восстановления.|Да|Простая (по умолчанию)|Создавайте резервную копию базы данных **msdb** после каждого ее обновления.|  
|[Resource](../../relational-databases/databases/resource-database.md) (RDB)|База данных только для чтения, которая содержит копии всех системных объектов, поставляемых с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|нет|-|База данных **Resource** находится в файле mssqlsystemresource.mdf, в котором содержится только код. Поэтому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создать резервную копию базы данных **Resource** .<br /><br /> Примечание. Рассматривая файл mssqlsystemresource.mdf как двоичный файл (EXE), а не файл базы данных, для создания его резервной копии можно выполнить простое резервное копирование файла или диска. Нельзя использовать восстановление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для резервных копий. Восстановить резервную копию файла mssqlsystemresource.mdf можно будет только вручную; при этом следует соблюдать осторожность, чтобы не перезаписать текущую базу данных **Resource** устаревшей или потенциально небезопасной версией.|  
|[tempdb](../../relational-databases/databases/tempdb-database.md)|Рабочая область для хранения временных или промежуточных результирующих наборов. Эта база данных создается заново при каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При отключении экземпляра сервера любые сведения, содержащиеся в базе данных **tempdb** , удаляются навсегда.|нет|Простая|Создать резервную копию системной базы данных **tempdb** нельзя.|  
|[Настройка распространения](../../relational-databases/replication/configure-distribution.md)|База данных, которая существует только в том случае, если сервер настроен как распространитель репликации. Эта база данных содержит метаданные и данные журнала для всех типов репликации, а также транзакции для репликации транзакций.|Да|Простая|Сведения о том, когда следует создавать резервные копии базы данных **distribution** , см. в статье [Создание резервной копии и восстановление из копий реплицируемых баз данных](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md).|  
  
 * Дополнительные сведения о текущей модели восстановления базы данных см. в статье [Просмотр или изменение модели восстановления базы данных (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) или [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
## <a name="limitations-on-restoring-system-databases"></a>Ограничения восстановления системных баз данных  
  
-   Системные базы данных могут быть восстановлены только из резервных копий, созданных той версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая запущена на данном экземпляре сервера. Например, чтобы восстановить системную базу данных на экземпляре сервера, работающего под [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1), необходимо использовать резервную копию базы данных, созданную после обновления экземпляра сервера до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1).  
  
-   Для восстановления любой базы данных должен быть запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для запуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо, чтобы база данных **master** была доступна и хотя бы частично пригодна к использованию. Если база данных **master** непригодна к использованию, ее можно вернуть в нормальное состояние следующими способами.  
  
    -   Восстановить базу данных **master** на основе актуальной резервной копии.  
  
         Если экземпляр сервера удалось запустить, базу данных **master** можно восстановить из полной резервной копии.  
  
    -   Перестроить базу данных **master** с нуля.  
  
         Если серьезное повреждение базы данных **master** не позволяет запустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], базу данных **master**нужно перестроить. Дополнительные сведения см. в разделе [Перестроение системных баз данных](../../relational-databases/databases/rebuild-system-databases.md).  
  
        > [!IMPORTANT]  
        >  При перестроении базы данных **master** все системные базы данных также перестраиваются.  
  
-   В некоторых случаях для проблем, связанных с восстановлением табличного шаблона базы данных модели, может потребоваться перестроение системных баз данных или замена MDF- и LDF-файлов базы данных модели. Дополнительные сведения см. в разделе [Перестроение системных баз данных](../../relational-databases/databases/rebuild-system-databases.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Выполнение полного восстановления базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
  
-   [Восстановление базы данных master (Transact-SQL)](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md)  
  
-   [Просмотр или изменение модели восстановления базы данных (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
-   [Перемещение системных баз данных](../../relational-databases/databases/move-system-databases.md)  
  
## <a name="see-also"></a>См. также:  
 [База данных распространителя](../../relational-databases/replication/distribution-database.md)   
 [База данных master](../../relational-databases/databases/master-database.md)   
 [База данных msdb](../../relational-databases/databases/msdb-database.md)   
 [База данных model](../../relational-databases/databases/model-database.md)   
 [База данных Resource](../../relational-databases/databases/resource-database.md)   
 [База данных tempdb](../../relational-databases/databases/tempdb-database.md)  
  
  
