---
title: "Модели восстановления (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 07/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database backups [SQL Server], recovery models
- bulk-logged recovery model [SQL Server]
- recovery [SQL Server], recovery model
- restoring transaction logs [SQL Server], recovery models
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], about
- transaction log backups [SQL Server]
- simple recovery model [SQL Server]
- backups [SQL Server], recovery models
- recovery models [SQL Server]
- recovery models [SQL Server], transaction log management
- database restores [SQL Server], recovery models
- transaction log restores [SQL Server]
- logs [SQL Server], recovery models
- restoring databases [SQL Server], recovery models
- full recovery model [SQL Server]
- backing up transaction logs [SQL Server], recovery models
ms.assetid: 8cfea566-8f89-4581-b30d-c53f1f2c79eb
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Active
ms.openlocfilehash: d8a6245577244eed484bdc3d370c0527942a282a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="recovery-models-sql-server"></a>Модели восстановления (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Операции резервного копирования и восстановления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются в контексте модели восстановления базы данных. Модели восстановления предназначены для управления обслуживанием журналов транзакций. *Модель восстановления* — это свойство базы данных, которое управляет процессом регистрации транзакций, определяет, требуется ли для журнала транзакций резервное копирование, а также определяет, какие типы операций восстановления доступны. Существует три модели восстановления: простая модель восстановления, модель полного восстановления и модель восстановления с неполным протоколированием. Обычно в базе данных используется модель полного восстановления или простая модель восстановления. Базу данных можно в любой момент переключить на использование другой модели восстановления.  
  
 **В этом разделе.**  
  
-   [Общие сведения о модели восстановления](#RMov)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="RMov"></a> Общие сведения о модели восстановления  
 В следующей таблице представлены сведения о трех моделях восстановления.  
  
|Модель восстановления|Description|Риск потери результатов работы|Восстановить до заданного момента времени?|  
|--------------------|-----------------|------------------------|-------------------------------|  
|**Простой**|Нет резервных копий журналов.<br /><br /> Автоматически освобождает место на диске, занятое журналами, устраняя таким образом необходимость в управлении размером журналов транзакций. Дополнительные сведения о резервном копировании базы данных в простой модели восстановления см. в разделе [Полные резервные копии базы данных (SQL Server)](../../relational-databases/backup-restore/full-database-backups-sql-server.md).<br /><br /> Операции, требующие резервного копирования журнала транзакций, не поддерживаются в простой модели восстановления. Следующие функции не могут быть использованы в простом режиме восстановления:<br /><br /> — Доставка журналов<br /><br /> — Группы AlwaysOn или зеркальное отображение базы данных<br /><br /> — Восстановление носителя без потери данных<br /><br /> — Восстановление на определенный момент времени|Изменения с момента создания последней резервной копии не защищены. В случае аварийной ситуации эти изменения придется вносить повторно.|Возможно восстановление только до конца резервной копии. Дополнительные сведения см. в разделе [Полное восстановление базы данных (простая модель восстановления)](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md). <br><br> Более подробное описание простой модели восстановления см. в статье [Простая модель восстановления SQL Server](https://www.mssqltips.com/sqlservertutorial/4/sql-server-simple-recovery-model/) , составленной ребятами из [MSSQLTips!](https://www.mssqltips.com)|  
|**Полный**|Необходимы резервные копии журналов.<br /><br /> Потеря результатов работы из-за повреждения файлов данных исключена.<br /><br /> Возможно восстановление до произвольного момента времени (например до ошибки приложения или пользователя). Дополнительные сведения о создании резервных копий базы данных с использованием полной модели восстановления см. в разделах [Полные резервные копии базы данных (SQL Server)](../../relational-databases/backup-restore/full-database-backups-sql-server.md) и [Полное восстановление базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md).|Обычно нет.<br /><br /> Если поврежден заключительный фрагмент журнала, то требуется восстановление изменений, произведенных в базе с момента создания последней резервной копии журналов.|Может выполнять восстановление до определенного момента времени при наличии всех необходимых резервных копий до этого момента времени. Дополнительные сведения об использовании резервных копий журналов для восстановления до точки сбоя см. в разделе [Восстановление базы данных SQL Server на определенный момент времени (полная модель восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).<br /><br /> Примечание. Если осуществляется работа с двумя или более базами данных с полным восстановлением, которые должны быть логически согласованными, для гарантии возможности восстановления этих баз данных, возможно, придется реализовать специальные процедуры. Дополнительные сведения см. в разделе [Восстановление связанных баз данных, которые содержат помеченную транзакцию](../../relational-databases/backup-restore/recovery-of-related-databases-that-contain-marked-transaction.md).|  
|**С неполным протоколированием**|Необходимы резервные копии журналов.<br /><br /> Дополнение к полной модели полного восстановления, позволяющее выполнять высокопроизводительные операции массового копирования.<br /><br /> Уменьшает место, занимаемое журналами, за счет неполного протоколирования большинства массовых операций. Сведения о том, к каким операциям можно применять минимальное протоколирование, см. в разделе [Журнал операций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md).<br /><br /> Дополнительные сведения о создании резервных копий базы данных с использованием модели восстановления с неполным протоколированием см. в разделах [Полные резервные копии базы данных (SQL Server)](../../relational-databases/backup-restore/full-database-backups-sql-server.md) и [Полное восстановление базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md).|Если журнал был поврежден или с момента создания последней резервной копии журналов выполнялись операции с неполным протоколированием, все изменения после этого резервного копирования необходимо внести повторно.<br /><br /> Если нет, результаты работы потеряны не будут.|Возможно восстановление до конца любой резервной копии. Восстановление до заданной точки не поддерживается.|  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Просмотр или изменение модели восстановления базы данных (SQL Server)](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
-   [Устранение неполадок при переполнении журнала транзакций (ошибка SQL Server 9002)](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>См. также:  
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Задачи автоматизированного администрирования (агент SQL Server)](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)  
  
  
