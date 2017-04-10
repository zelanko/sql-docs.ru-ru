---
title: "Выбор метода обновления компонента Database Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e57a427-2e88-4ef6-b142-4ccad97bcecc
caps.latest.revision: 23
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 23
---
# Выбор метода обновления компонента Database Engine
  Существует несколько подходов, которые следует учитывать при планировании обновления компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] предыдущего выпуска SQL Server до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , чтобы свести к минимуму время простоя и риски. Можно выполнить обновление на месте, миграцию в новую установку или последовательное обновление. Следующая схема поможет вам выбрать один из этих подходов. Каждый из подходов, указанных в схеме, кроме того, обсуждается ниже. Чтобы получить дополнительные сведения о точках принятия решений в этой схеме, ознакомьтесь с разделом [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
 ![Database Engine Upgrade Method Decision Tree](../../database-engine/install-windows/media/database-engine-upgrade-method-decision-tree.png "Database Engine Upgrade Method Decision Tree")  
  
 **Загрузить**  
  
-   Чтобы скачать [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], перейдите на сайт  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
  
-   Есть учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016ctp2evaluationwindowsserver2012r2/?wt.mc_id=sqL16_vm)** , чтобы запустить виртуальную машину с уже установленным [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
> [!NOTE]  
>  При составлении плана обновления, кроме того, можно рассмотреть возможность обновления базы данных SQL Azure или виртуализации среды SQL Server. Эти темы выходят за рамки данного раздела, однако вы можете ознакомиться со следующими статьями: [Вводные сведения о гибридном облаке SQL Server 2016](../Topic/Introduction%20to%20SQL%20Server%202016%20Hybrid%20Cloud.md), [Обзор SQL Server на виртуальных машинах Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/), [База данных SQL Azure](https://azure.microsoft.com/en-us/services/sql-database/) и [Варианты установки SQL Server в Azure](https://azure.microsoft.com/documentation/articles/data-management-azure-sql-database-and-sql-server-iaas/).  
  
##  <a name="UpgradeInPlace"></a> Обновление на месте  
 В этом случае программа установки SQL Server обновляет существующую установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , заменяя существующие биты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] битами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , а затем обновляет все системные и пользовательские базы данных.  Обновление на месте — это самый простой метод, подразумевающий некоторое время простоя; в случае необходимости отката он занимает больше времени, кроме того, этот вариант поддерживается не для всех сценариев. Дополнительные сведения о поддерживаемых и неподдерживаемых сценариях обновления на месте см. в разделе [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Этот подход часто используется в следующих сценариях:  
  
-   среда разработки без конфигурации высокой доступности;  
  
-   рабочая среда без критически важных нагрузок, которая допускает некоторое время простоя и в которой используется новое оборудование и программное обеспечение. Время простоя зависит от размера базы данных и быстродействия подсистемы ввода-вывода. Обновление SQL Server 2014 при использовании оптимизированных для памяти таблиц займет немного больше времени. Дополнительные сведения см. в разделе [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
> [!WARNING]  
>  При запуске программы установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] останавливается и перезапускается в процессе выполнения предварительных проверок.  
  
> [!CAUTION]  
>  При обновлении версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет перезаписан и перестанет существовать на компьютере. Перед обновлением создайте резервную копию баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и других объектов, связанных с экземпляром предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Следующая схема содержит обобщенный обзор действий, необходимых для обновления [!INCLUDE[ssDE](../../includes/ssde-md.md)] на месте.  
  
 ![Database Engine Upgrade Non-HA In-Place Upgrade](../../database-engine/install-windows/media/database-engine-upgrade-non-ha-in-place-upgrade.png "Database Engine Upgrade Non-HA In-Place Upgrade")  
  
 Дополнительные сведения см. в статье [Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md).  
  
##  <a name="NewInstallationUpgrade"></a> Миграция в новую установку  
 В этом случае сохраняется текущая среда и выполняется построение новой среды [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , зачастую на новом оборудовании и с новой версией операционной системы. После установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в новой среде выполняется ряд действий по подготовке новой среды, чтобы можно было перенести имеющиеся пользовательские базы данных из текущей среды в новую среду и свести к минимуму время простоя. Эти действия включают перенос следующих компонентов.  
  
-   **Системные объекты**. Некоторые приложения зависят от информации, сущностей или объектов, которые находятся вне области однопользовательской базы данных. Как правило, приложение зависит от баз данных master и msdb и пользовательской базы данных. Что-либо сохраненное вне пользовательской базы данных, которая требуется для правильного функционирования другой базы данных, должно быть доступно на экземпляре целевого сервера. Например, имена входа для приложений сохраняются как метаданные в базе данных master и должны быть созданы заново на целевом сервере. Если приложение или план обслуживания базы данных зависит от заданий агента SQL Server, чьи метаданные сохранены в базе данных msdb, необходимо заново создать эти задания в экземпляре целевого сервера. Точно так же метаданные сохраняются в базе данных master для триггера уровня сервера.  
    При перемещении базы данных для приложения в другой экземпляр сервера необходимо повторно создать все метаданные зависимых сущностей и объектов в базах данных master и msdb в экземпляре целевого сервера. Например, если в приложении базы данных используются триггеры уровня сервера, то простого присоединения или восстановления базы данных в новой системе будет недостаточно. Функциональность базы данных не будет соответствовать ожидаемой, пока метаданные для этих триггеров в базе данных master не будут повторно созданы вручную. Дополнительные сведения см. в разделе [Управление метаданными при обеспечении доступности базы данных на другом экземпляре сервера (SQL Server)](../../relational-databases/databases/manage metadata when making a database available on another server.md).  
  
-   **Пакеты служб Integration Services, хранимые в базе данных MSDB** . Если пакеты хранятся в базе данных MSDB, потребуется записать эти пакеты в сценарий с помощью [dtutil Utility](../../integration-services/dtutil-utility.md) или повторно развернуть их на новом сервере. Прежде чем использовать пакеты на новом сервере, потребуется обновить их до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
-   **Ключи шифрования служб Reporting Services**. Одним из важных аспектов настройки сервера отчетов является создание резервной копии симметричного ключа, используемого для шифрования конфиденциальных данных. Резервная копия ключа требуется для выполнения многих распространенных операций и позволяет повторно использовать базу данных существующего сервера отчетов в новом сервере. Дополнительные сведения см. в разделах [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md) и [Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Поскольку новая среда   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] имеет те же системные объекты, что и текущая среда, потребуется выполнить миграцию пользовательских баз данных из существующей системы в экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] таким способом, который позволит свести к минимуму время простоя в существующей системе. Выполнить перенос базы данных можно с помощью резервного копирования и восстановления или перенаправления LUN в среде SAN. В приведенных ниже схемах приводятся этапы обоих методов.  
  
> [!CAUTION]  
>  Время простоя зависит от размера базы данных и быстродействия подсистемы ввода-вывода. Обновление SQL Server 2014 при использовании оптимизированных для памяти таблиц займет немного больше времени. Дополнительные сведения см. в разделе [Plan and Test the Database Engine Upgrade Plan](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
 После переноса пользовательской базы данных перенаправьте новых пользователей в новый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью одного из имеющихся методов (например, переименовав сервер, используя запись DNS или изменив строки подключения).  Метод новой установки сокращает риски и время простоя по сравнению с обновлением на месте и упрощает обновление оборудования и операционной системы, необходимые для обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Если уже имеется решение высокой доступности или какие-либо другие среды с несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], перейдите к разделу [Последовательное обновление](#RollingUpgrade). Если решения высокой доступности нет, можно временно настроить [зеркальное отображение базы данных](http://msdn.microsoft.com/library/ms190941.aspx), чтобы дополнительно сократить время простоя для упрощения обновления, или воспользоваться этой возможностью для настройки [группы доступности AlwaysOn](http://msdn.microsoft.com/library/hh510260.aspx) в качестве постоянного решения высокой доступности.  
  
 Например, этот подход можно использовать для обновления:  
  
-   установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в неподдерживаемой операционной системе;  
  
-   установки SQL Server для архитектуры x86, поскольку [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает установки x86;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на новом оборудовании или в новой версии операционной системы.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в сочетании с консолидацией серверов;  
  
-   SQL Server 2005, поскольку [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает обновление на месте выпуска SQL Server 2005 до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Are you upgrading from SQL Server 2005?](../../database-engine/install-windows/are-you-upgrading-from-sql-server-2005.md).  
  
 Действия, необходимые для обновления методом новой установки, немного различаются в зависимости от того, используется ли подключенное хранилище или хранилище SAN.  
  
-   **Среда с подключенным хранилищем** . При наличии среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующей подключенное хранилище, ознакомьтесь со следующей схемой и ссылками на схеме, которые описывают действия, необходимые для обновления путем новой установки [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
     ![New installation upgrade method using backup and restore for attached storage](../../database-engine/install-windows/media/new-installation-upgrade-method-using-backup-and-restore-for-attached-storage.png "New installation upgrade method using backup and restore for attached storage")  
  
-   **Среда с хранилищем SAN**  . При наличии среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующей хранилище SAN, ознакомьтесь со следующей схемой и ссылками на схеме, которые описывают действия, необходимые для обновления путем новой установки [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
     ![New installation upgrade method using detach and attach for SAN storage](../../database-engine/install-windows/media/new-installation-upgrade-method-using-detach-and-attach-for-san-storage.png "New installation upgrade method using detach and attach for SAN storage")  
  
##  <a name="RollingUpgrade"></a> Последовательное обновление  
 Последовательное обновление требуется в средах SQL Server с несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые должны быть обновлены в определенном порядке для сокращения времени простоя и рисков и сохранения функциональности среды. Последовательное обновление является, по существу, обновлением нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в определенном порядке путем обновления на месте каждого имеющегося экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или путем новой установки (что упрощает обновление оборудования и операционной системы в рамках проекта обновления среды). Существует ряд сценариев, в которых необходимо использовать метод последовательного обновления. Все они описаны в следующих разделах:  
  
-   Группы доступности AlwaysOn. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Обновление экземпляров реплики группы доступности AlwaysOn](../../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).  
  
-   Экземпляры отказоустойчивой кластеризации. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Обновление экземпляра отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md).  
  
-   Зеркальные экземпляры. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Обновление зеркальных экземпляров](../../database-engine/database-mirroring/upgrading-mirrored-instances.md).  
  
-   Экземпляры доставки журналов. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Обновление доставки журналов до SQL Server 2016 (Transact-SQL)](../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md).  
  
-   Среда репликации. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md).  
  
-   Масштабируемая среда SQL Server Reporting Services. Подробное описание процедуры последовательного обновления в этой среде см. в разделе [Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
## Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Choose%20a%20Database%20Engine%20Upgrade%20Method%20page).  
  
## См. также:  
 [Составление и тестирование плана обновления Database Engine](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md)   
 [Завершение обновления ядра СУБД](../../database-engine/install-windows/complete-the-database-engine-upgrade.md)  
  
  