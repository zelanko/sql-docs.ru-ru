---
title: "Синхронизация данных | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ccda32ba9e85f698a2a642d2dd52773e78ae6d06
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="synchronize-data"></a>Синхронизация данных
  Под синхронизацией данных подразумевается процесс распространения изменений данных и схем между издателем и подписчиками, после того как был применен исходный моментальный снимок на подписчике. Синхронизация может происходить:  
  
-   Непрерывно, что типично для репликации транзакций.  
  
-   По требованию, что типично для репликации слиянием.  
  
-   По расписанию, что типично для репликации моментальных снимков.  
  
 Когда подписка синхронизируется, в зависимости от используемого типа репликации происходят разные процессы:  
  
-   Репликация моментальных снимков. Синхронизация означает, что агент распространителя повторно применяет моментальный снимок на подписчике — так, чтобы схема и данные в базе данных подписки были согласованы со схемой и данными в базе данных публикации.  
  
     Если на издателе были произведены изменения данных или схемы, для распространения изменений на подписчик должен быть создан новый моментальный снимок.  
  
-   Репликация транзакций. Синхронизация означает, что агент распространителя передает на подписчик обновления, вставки, удаления и любые другие изменения из базы данных распространителя.  
  
-   Репликация слиянием. Синхронизация означает, что агент слияния передает изменения с подписчика на издатель, а затем передает изменения с издателя на подписчик. Конфликты, если они присутствуют, обнаруживаются и разрешаются. Выполняется конвергенция данных, а издатель и все подписчики в итоге достигают состояния с одинаковыми значениями данных. Если были обнаружены и разрешены конфликты, работа, зафиксированная некоторыми из пользователей, изменяется, чтобы разрешить конфликт в соответствии с определенными правилами.  
  
 Публикации моментальных снимков полностью обновляют схему на подписчике при каждой синхронизации, так что все изменения схемы применяются на подписчике. Репликация транзакций и репликация слиянием также поддерживают наиболее распространенные изменения схем. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Сведения о синхронизации принудительной подписки см. в разделе [синхронизации принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
 Сведения о синхронизации подписки по запросу см. в разделе [синхронизации подписки по запросу](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
 Чтобы настроить расписания синхронизации, см. раздел [укажите расписания синхронизации](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 **Просмотр и разрешение конфликтов синхронизации**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Просмотр конфликтов данных для публикаций транзакций (среда SQL Server Management Studio)](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## <a name="executing-code-during-synchronization"></a>Выполнение кода во время синхронизации  
 Репликация поддерживает два метода выполнения кода во время синхронизации  
  
-   Выполнение скрипта по запросу поддерживается для репликации транзакций и репликации слиянием. С помощью выполнения скрипта по запросу можно указать, какой скрипт SQL будет выполняться во время синхронизации. скрипт копируется на подписчик и выполняется с помощью программы **sqlcmd** в начале процесса синхронизации. скрипт не имеет доступа к реплицированным изменениям, когда они применяются к подписчику. Дополнительные сведения см. в статье [Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Обработчики бизнес-логики поддерживаются для репликации слиянием. С помощью платформы обработчиков бизнес-логики можно создать сборку управляемого кода, которая будет вызываться в процессе синхронизации слиянием. Сборка включает бизнес-логику, которая может учитывать ряд условий во время синхронизации: изменения данных, конфликты и ошибки. Дополнительные сведения см. в статье [Выполнение бизнес логики при синхронизации слиянием](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## <a name="see-also"></a>См. также:  
 [Обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
