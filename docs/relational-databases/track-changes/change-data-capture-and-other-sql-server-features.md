---
title: Отслеживание измененных данных и другие функции SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: track-changes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], other SQL Server features and
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
caps.latest.revision: 14
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 29c9a2ee3c323c9689e7ece0b2b1318a7051321e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33011741"
---
# <a name="change-data-capture-and-other-sql-server-features"></a>Система отслеживания измененных данных и другие функции SQL Server
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается взаимодействие следующих функций и системы отслеживания измененных данных.  
  
-   [Отслеживание изменений](#ChangeTracking)  
  
-   [Зеркальное отображение базы данных](#DatabaseMirroring)  
  
-   [Репликация транзакций](#TransReplication)  
  
-   [Восстановление или прикрепление базы данных, активированной для системы отслеживания измененных данных](#RestoreOrAttach)  
  
##  <a name="ChangeTracking"></a> Change Tracking  
 Отслеживание измененных данных и [отслеживание изменений](../../relational-databases/track-changes/about-change-tracking-sql-server.md) можно активировать на одной и той же базе данных. Никаких особых предосторожностей не требуется. Дополнительные сведения см. в разделе [Работа с отслеживанием изменений (SQL Server)](../../relational-databases/track-changes/work-with-change-tracking-sql-server.md).  
  
##  <a name="DatabaseMirroring"></a> Зеркальное отображение базы данных  
 Для базы данных, активированной для отслеживания измененных данных, можно установить зеркальное отображение. Чтобы обеспечить автоматическое выполнение отслеживания и очистки после отработки отказа, выполните следующие шаги.  
  
1.  Убедитесь, что запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на новом экземпляре основного сервера.  
  
2.  Создайте задание отслеживания и задание очистки в новой основной базе данных (ранее зеркальной базе данных). Создание заданий выполняйте с помощью хранимой процедуры [sp_cdc_add_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md) .  
  
 Для просмотра текущей конфигурации задания очистки или отслеживания пользуйтесь хранимой процедурой [sys.sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md) в новом экземпляре основного сервера. Для конкретной базы данных задание отслеживания называется cdc.*имя_базы_данных*_capture, а задание очистки — cdc.*имя_базы_данных*_cleanup, где *имя_базы_данных* — имя базы данных.  
  
 Для изменения конфигурации задания пользуйтесь хранимой процедурой [sys.sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md).  
  
 Сведения о зеркальном отображении базы данных см. в разделе [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
##  <a name="TransReplication"></a> Transactional Replication  
 Система отслеживания измененных данных и репликация транзакций могут сосуществовать в одной базе данных, но если обе эти функции были включены, то заполнение таблиц изменений будет выполняться другим способом. Для считывания изменений из журнала транзакций система отслеживания измененных данных и репликация транзакций всегда используют одну и ту же процедуру [sp_replcmds](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md). Если система отслеживания измененных данных включена отдельно, то процедуру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_replcmds **вызывает задание агента**. Если в базе данных включены обе эти функции, процедуру **sp_replcmds**вызывает агент чтения журнала. Агент заполняет как таблицы изменений, так и таблицы базы данных распространителя. Дополнительные сведения см. в статье [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md).  
  
 Рассмотрим случай, когда для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] была включена система отслеживания измененных данных и две таблицы были включены для отслеживания. Для заполнения таблиц изменений задание отслеживания вызывает процедуру **sp_replcmds**. База данных активируется для репликации транзакций, после этого создается публикация. Для базы данных создается агент чтения журнала, задание отслеживания удаляется. Агент чтения журнала продолжает просматривать журнал, начиная с последнего регистрационного номера транзакции, зафиксированного в таблице изменений. Это обеспечивает согласованность данных в таблицах изменений. Если в данной базе данных будет отключена репликация транзакций, то агент чтения журнала будет удален, а задание отслеживания будет создано повторно.  
  
> [!NOTE]  
>  Если для системы отслеживания измененных данных и репликации транзакций используется агент чтения журнала, то в базу данных распространителя в первую очередь записываются реплицированные изменения. Затем в таблицы изменений записываются отслеженные изменения. Обе операции фиксируются одновременно. Если при записи в базу данных распространителя возникла задержка, то перед появлением изменений в таблицах изменений пройдет такое же время.  
  
 Параметр **proc exec** репликации транзакций недоступен, когда включена система отслеживания измененных данных.  
  
##  <a name="RestoreOrAttach"></a> Восстановление или прикрепление базы данных, активированной для системы отслеживания измененных данных  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется следующая логика.  
  
-   Если база данных восстанавливается на том же сервере с таким же именем базы данных, то система отслеживания измененных данных останется активированной.  
  
-   Если база данных восстанавливается на другом сервере, то по умолчанию система отслеживания измененных данных будет отключена, а все связанные метаданные будут удалены.  
  
     Для сохранения системы отслеживания измененных данных в активированном состоянии при восстановлении базы данных следует использовать параметр **KEEP_CDC** . Дополнительные сведения об этом параметре см. в разделе [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md).  
  
-   Если база данных отсоединяется и присоединяется к тому же или другому серверу, то система отслеживания измененных данных остается активированной.  
  
-   Если база данных присоединяется или восстанавливается с параметром **KEEP_CDC** в любом выпуске, отличном от выпуска Enterprise, то эта операция будет заблокирована, так как для системы отслеживания измененных данных требуется выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise. Отображается сообщение об ошибке 934.  
  
     `SQL Server cannot load database '%.*ls' because Change Data Capture is enabled. The currently installed edition of SQL Server does not support Change Data Capture. Either restore database without KEEP_CDC option, or upgrade the instance to one that supports Change Data Capture.`  
  
 Процедуру [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md) можно использовать для отключения отслеживания измененных данных в восстановленной или присоединенной базе данных.  
  
## <a name="change-data-capture-and-always-on"></a>Система отслеживания измененных данных и AlwaysOn  
 При использовании AlwaysOn перечисление изменений необходимо выполнять во вторичной реплике для уменьшения загрузки диска в первичной.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование и наблюдение за отслеживанием измененных данных (SQL Server)](../../relational-databases/track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
