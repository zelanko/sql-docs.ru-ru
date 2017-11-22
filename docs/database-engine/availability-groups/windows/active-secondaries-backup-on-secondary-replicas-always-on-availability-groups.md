---
title: "Активные вторичные реплики: резервное копирование во вторичных репликах (группы доступности AlwaysOn) | Документы Майкрософт"
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
caps.latest.revision: "34"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 7bdc1156dc782aab3e2cd244c1ca6b318015089e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a>Активные вторичные реплики, резервное копирование во вторичных репликах (группы доступности AlwaysOn)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Функции [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] по поддержке вторичных реплик обеспечивают выполнение операций резервного копирования для вторичных реплик. Операции резервного копирования могут оказывать значительную нагрузку на систему ввода-вывода и ЦП (при использовании сжатия резервных копий). Перенос резервного копирования в синхронизированную или синхронизирующуюся вторичную реплику позволяет использовать ресурсы на экземпляре сервера, где размещается первичная реплика, для рабочей нагрузки первого уровня.  

> [!NOTE]  
>  Инструкция RESTORE недопустима для базы данных-источника или базы данных-получателя группы доступности.  
  
-   [Поддерживаемые типы резервного копирования](#SupportedBuTypes)  
  
-   [Настройка места выполнения заданий резервного копирования](#WhereBuJobsRun)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="SupportedBuTypes"></a> Поддерживаемые типы резервного копирования на вторичных репликах  
  
-   **BACKUP DATABASE** поддерживает только полные, доступные только для копирования резервные копии баз данных, файлов и файловых групп, которые выполняются во вторичных репликах. Обратите внимание, что резервные копии, доступные только для копирования, не влияют на цепочку журналов и не очищают битовую карту разностного резервного копирования.  
  
-   Разностные резервные копии не поддерживаются во вторичных репликах.  
  
-   **BACKUP LOG** поддерживает только обычное резервное копирование журналов (параметр COPY_ONLY не поддерживается для резервных копий журналов во вторичных репликах).  
  
     Обеспечивается последовательная цепочка журналов по всем резервным копиям журналов в любой реплике (первичной или вторичной) независимо от их режима доступности (синхронной или асинхронной фиксации).  
  
-   Для выполнения резервного копирования базы данных-получателя вторичная реплика должна быть способна обмениваться данными с первичной репликой и находиться в состоянии **SYNCHRONIZED** или **SYNCHRONIZING**.  

В распределенной группе доступности резервное копирование может выполняться во вторичных репликах в той же группе доступности, что и активная первичная реплика, или в первичной реплике любой вторичной группы доступности. Резервное копирование не может выполняться во вторичной реплике вторичной группы доступности, так как вторичные реплики могут обмениваться данными только с первичной репликой в их собственной группе доступности. Выполнять операции резервного копирования могут только реплики, которые взаимодействуют с глобальной первичной репликой напрямую.

##  <a name="WhereBuJobsRun"></a> Настройка места выполнения заданий резервного копирования  
 Выполнение резервного копирования во вторичной реплике для снятия рабочей нагрузки резервного копирования с основного рабочего сервера обеспечивает значительные преимущества. Однако выполнение резервного копирования на вторичных репликах создает значительные сложности в процессе определения, где должны запускаться задания резервного копирования. Для решения этой проблемы настройте расположение запуска заданий резервного копирования, как описано далее.  
  
1.  Настройте группу доступности, чтобы указать, на каких репликах доступности предпочтительно проведение резервного копирования. Дополнительные сведения см. в описании параметров *AUTOMATED_BACKUP_PREFERENCE* и *BACKUP_PRIORITY* в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/create-availability-group-transact-sql.md) или [ALTER AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
2.  Создайте скрипты заданий резервного копирования для каждой из баз данных доступности на каждом экземпляре сервера, на котором размещается реплика доступности, потенциально используемая для выполнения резервного копирования. Дополнительные сведения см. в подразделе "Дальнейшие действия. После настройки резервного копирования во вторичных репликах" раздела [Настройка резервного копирования в репликах доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Настройка резервного копирования во вторичных репликах**  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
 **Определение, является ли текущая реплика предпочитаемой репликой резервного копирования**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](../../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md)  
  
 **Создание задания резервного копирования**  
  
-   [Использование мастера планов обслуживания](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [Реализация заданий](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Резервные копии только для копирования (SQL Server)](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
