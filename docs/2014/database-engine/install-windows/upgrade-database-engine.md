---
title: Обновление ядра СУБД | Документы Майкрософт
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84f032e89730aa9828dada1208c6d794db97260b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774985"
---
# <a name="upgrade-database-engine"></a>Обновление [компонент ядра СУБД]
  В данном разделе содержатся сведения, которые понадобятся для понимания процесса обновления при подготовке к нему. Он состоит из следующих подразделов.  
  
-   Известные проблемы, связанные с обновлением.  
  
-   Задачи и вопросы, предшествующие обновлению.  
  
-   Ссылки на методические разделы по обновлению компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Ссылки на методические разделы по миграции баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Вопросы, касающиеся отказоустойчивых кластеров.  
  
-   Задачи и вопросы, следующие за обновлением.  
  
## <a name="known-upgrade-issues"></a>Известные проблемы, связанные с обновлением  
 Прежде чем приступать к обновлению компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], ознакомьтесь с разделом [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md). Дополнительные сведения о поддерживаемых сценариях обновления и известных проблемах обновления см. в разделе [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades.md). Сведения об обратной совместимости других компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Backward Compatibility](../../getting-started/backward-compatibility.md).  
  
> [!IMPORTANT]  
>  Если обновление производится с одного выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до другого, то сначала проверьте, поддерживаются ли в целевом выпуске все используемые функции.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с предыдущей версии выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise выберите "Enterprise Edition: лицензирование по числу ядер" и "Enterprise Edition". Эти выпуски Enterprise отличаются только режимом лицензирования. Дополнительные сведения см. в разделе [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
## <a name="pre-upgrade-checklist"></a>Контрольный список действий перед обновлением  
 Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает обновление предыдущей версии до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Есть также возможность выполнить миграцию баз данных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Миграция может быть произведена из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в другой на том же компьютере или из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой компьютер. Произвести ее можно следующими способами: при помощи мастера копирования баз данных, функций резервного копирования и восстановления, мастера импорта и экспорта служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], а также при помощи массового экспорта и импорта.  
  
 Перед обновлением компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]просмотрите следующие источники:  
  
-   Обратитесь к разделу [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Обратитесь к разделу [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md).  
  
-   Обратитесь к разделу [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Обратитесь к разделу [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades.md).  
  
-   Обратитесь к разделу [Использование помощника по обновлению для подготовки к обновлениям](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   Обратитесь к разделу [Использование программы распределенного воспроизведения для подготовки обновлений](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md).  
  
-   Обратитесь к разделу [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).  
  
-   Обратитесь к разделу [Перенос планов запросов](change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
 Прежде чем приступать к обновлению до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ознакомьтесь со следующими соображениями и сделайте соответствующие изменения.  
  
-   При обновлении экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил связи MSX/TSX, обновите целевые серверы перед обновлением главных серверов. Если обновить главные серверы раньше целевых серверов, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сможет подключиться к главным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   При переходе с 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на 64-разрядную версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо обновить до компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Создайте резервные копии всех файлов баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляемых экземпляров, чтобы при необходимости можно было восстановить их.  
  
-   Выполните в обновляемых базах данных соответствующие команды DBCC, чтобы убедиться в том, что они находятся в согласованном состоянии.  
  
-   Оцените, сколько места на диске, помимо занимаемого пользовательскими базами данных, понадобится для обновления компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о том, сколько места на диске занимают компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Убедитесь в том, что существующие системные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (master, model, msdb и tempdb) настроены для автоувеличения и что для них имеется достаточно места на диске.  
  
-   Убедитесь в том, что все серверы баз данных имеют регистрационные данные для входа в базу данных master. Это важно для восстановления базы данных, поскольку системные регистрационные данные для входа хранятся в базе данных master.  
  
-   Отключите все хранимые процедуры, запускаемые при старте системы; это необходимо, поскольку процесс обновления будет останавливать и запускать службы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемом обновлению. Хранимые процедуры, запускаемые при старте системы, могут блокировать процесс обновления.  
  
-   Убедитесь, что репликация обновлена и остановите репликацию.  
  
-   Закройте все приложения, а также службы, имеющие зависимости от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При наличии локальных приложений, подключенных к обновляемому экземпляру, процесс обновления может завершиться ошибкой.  
  
-   Если используется зеркальное отображение базы данных, см. раздел [Снижение времени простоя зеркальных баз данных при обновлении экземпляров сервера](../database-mirroring/upgrading-mirrored-instances.md).  
  
## <a name="upgrading-the-database-engine"></a>Обновление компонента Database Engine  
 Установка [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии может быть перезаписана посредством обновления версии. Если при запуске программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружена предыдущая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , все программные файлы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновятся, но при этом сохранятся все данные экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Кроме того, останутся без изменений предыдущие версии электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!WARNING]  
>  При запуске программы установки SQL Server 2014 экземпляр SQL Server останавливается и перезапускается в процессе выполнения предварительных проверок.  
  
> [!CAUTION]  
>  При обновлении версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предыдущий экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет перезаписан и перестанет существовать на компьютере. Перед обновлением создайте резервную копию баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и других объектов, связанных с экземпляром предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Обновление компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно выполнить при помощи мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="database-compatibility-level-after-upgrade"></a>Уровень совместимости баз данных после обновления  
 После обновления уровни совместимости баз `tempdb`данных `model`ресурсов `msdb` , **Resource** и устанавливаются в 120. Системная база данных `master` сохраняет уровень совместимости, который она имела до обновления.  
  
 Если уровень совместимости пользовательской базы данных до обновления был 100 или выше, после обновления он останется таким же. Если уровень совместимости до обновления был 90, в обновленной базе данных он устанавливается в значение 100, что является минимально поддерживаемым уровнем совместимости в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Новые пользовательские базы данных наследуют уровень совместимости базы данных `model`.  
  
## <a name="migrating-databases"></a>Миграция баз данных  
 Переместить пользовательские базы данных на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно при помощи функций резервного копирования и восстановления либо с помощью функций отсоединения и присоединения, предоставляемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Копирование баз данных путем создания и восстановления резервных копий](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) или [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
> [!IMPORTANT]  
>  Перемещение и копирование базы данных, которая имеет одинаковые имена на исходном и целевом серверах, невозможно. В этом случае она будет помечена как уже существующая.  
  
 Дополнительные сведения см. в статье [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="after-upgrading-the-database-engine"></a>После обновления компонента Database Engine  
 После обновления компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]выполните следующие действия.  
  
-   Повторно зарегистрируйте серверы. Дополнительные сведения о регистрации серверов см. в разделе [Регистрация серверов](../../ssms/register-servers/register-servers.md).  
  
-   Для обеспечения семантической согласованности результатов запроса заполните полнотекстовые каталоги повторно.  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] устанавливает новые средства разбиения по словам, используемые компонентами полнотекстового и семантического поиска. Средства разбиения по словам используются как во время индексирования, так и при выполнении запросов. Если не выполнить перепостроение полнотекстовых каталогов, результаты поиска могут быть несогласованными. Полнотекстовый запрос, выполняющий поиск фразы, которая в предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была разбита средством разбиения по словам не так, как это сделано текущим средством разбиения по словам, может не обнаружить документ или строку, содержащую эту фразу. Это связано с тем, что индексированные фразы были разбиты с помощью логики, которая не соответствует логике, используемой в запросе. Решение заключается в том, чтобы заполнить полнотекстовые каталоги повторно (перестроить их) с помощью новых средств разбиения по словам, чтобы при индексировании и выполнении запросов использовалась одинаковая логика.  
  
     Дополнительные сведения см. в разделе [sp_fulltext_catalog (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql).  
  
-   Настройте установку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы сократить уязвимую для атак контактную зону системы, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выборочно устанавливает и активирует ключевые службы и функции.  
  
-   Проверьте или удалите подсказки USE PLAN, которые формируются [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и применяются в запросах для секционированных таблиц и индексов.  
  
     В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] изменился способ обработки запросов к страницам секционированных таблиц и индексов. Запросы к секционированным объектам с указанием USE PLAN для планов, сформированных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , могут оказаться несовместимыми с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. После выполнения обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется выполнить следующие процедуры.  
  
     **Если подсказка USE PLAN указана непосредственно в запросе**  
  
    1.  Удалите указание USE PLAN из запроса.  
  
    2.  Проверьте работу запроса.  
  
    3.  Если оптимизатор не выбрал подходящий план, настройте запрос и затем укажите подсказку USE PLAN с нужным планом запроса.  
  
     **Если подсказка USE PLAN указана непосредственно в структуре плана**  
  
    1.  При помощи функции sys.fn_validate_plan_guide проверьте правильность структуры плана. Кроме того, проверить недопустимые планы можно в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]по событию Plan Guide Unsuccessful.  
  
    2.  Если структура плана неверна, удалите ее. Если оптимизатор не выбрал подходящий план, настройте запрос и укажите указание USE PLAN с нужным планом запроса.  
  
     Если в структуре плана USE PLAN указан неверный план, это не приведет к ошибке выполнения. Вместо этого запрос будет скомпилирован без учета указания.  
  
 Любые базы данных, в которых возможность использования полнотекстовых каталогов была включена или отключена до обновления, сохранят этот статус после обновления. После обновления полнотекстовые каталоги будут перестроены и автоматически заполнены для всех баз данных с включенной возможностью использования полнотекстовых каталогов. Выполнение этой операции требует много времени и ресурсов. Можно временно приостановить проведение полнотекстового индексирования, выполнив следующую инструкцию.  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 1;  
```  
  
 Для возобновления заполнения полнотекстового индекса выполните следующую инструкцию.  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 0;  
```  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades.md)   
 [Работа с несколькими версиями и экземплярами SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [Обратная совместимость](../../getting-started/backward-compatibility.md)   
 [Обновление реплицируемых баз данных](upgrade-replicated-databases.md)  
  
  
