---
title: Новые&#39;(ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5e51cda61bb44d1f143cab50901276b927cca73a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176076"
---
# <a name="what39s-new-database-engine"></a>Новые&#39;(ядро СУБД)
  В этом последнем выпуске [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] появились новые средства и усовершенствования, которые расширяют возможности и повышают производительность архитекторов, разработчиков и администраторов, занимающихся проектированием, созданием и обслуживанием систем хранения данных. Ниже перечислены улучшения, внесенные в компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] .  
  
##  <a name="Feature"></a>Усовершенствованные функции ядро СУБД  
  
###  <a name="MemoryOpt"></a>Оптимизированные для памяти таблицы  
 In-Memory OLTP — это оптимизированное для памяти ядро СУБД, встроенное в модуль [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Ядро In-Memory OLTP оптимизировано для OLTP. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
 
  
###  <a name="DataFiles"></a>SQL Server файлы данных в Azure  
 [SQL Server файлы данных в Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) обеспечивает встроенную поддержку [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] файлов базы данных, хранящихся в виде больших двоичных объектов Azure. Эта функция позволяет создать базу данных в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] локальной среде или на виртуальной машине в Azure с выделенным местом хранения для данных в хранилище BLOB-объектов Azure.  
  
  
###  <a name="AzureVM"></a>Размещение базы данных SQL Server на виртуальной машине Azure  
 Используйте мастер [развертывания SQL Server базы данных в виртуальной машине Azure](https://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx) для размещения базы данных из экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на виртуальной машине Azure.  
  
  
###  <a name="Backup"></a>Усовершенствования резервного копирования и восстановления  
 
  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит следующие усовершенствования для функций резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   **Резервное копирование в SQL Server по URL-адресу**  
  
     Возможность резервного копирования на URL-адрес для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] была введена в версии [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) CU2, поддерживаемой только в [!INCLUDE[tsql](../includes/tsql-md.md)], PowerShell и SMO. В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] можно использовать [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для резервного копирования или восстановления из службы хранилища BLOB-объектов Azure. Новый параметр доступен как для задачи резервного копирования, так и для планов обслуживания. Дополнительные сведения см. в статьях [Использование задачи резервного копирования в SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS), [SQL Server резервное копирование на URL-адрес с помощью мастера планов обслуживания](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz)и [Восстановление из хранилища Azure с помощью SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS).  
  
-   **Управляемое резервное копирование SQL Server в Azure**  
  
     Служба [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] построена на основе функции резервного копирования на URL-адрес для [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] . В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] она применяется для управления и планирования операций резервного копирования баз данных и журналов. В этом выпуске поддерживается только резервное копирование в хранилище Azure. 
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] можно настроить и в базе данных и на уровне экземпляра и что для детального элемента управления на уровне базы данных и автоматизируя на уровне экземпляра. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]можно настроить для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] экземпляров, работающих локально, и экземпляров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , работающих на виртуальных машинах Azure. Рекомендуется использовать [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] экземпляры, работающие на виртуальных машинах Azure. Дополнительные сведения см. [в статье SQL Server управляемое резервное копирование в Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
-   **Шифрование для резервных копий**  
  
     Теперь можно выбрать, чтобы зашифровать файл резервной копии во время операции резервного копирования.  Она поддерживает несколько алгоритмов шифрования AES, включая 128 192, алгоритм AES 256 и Triple DES. Необходимо использовать сертификат или асимметричный ключ для шифрования во время резервного копирования. Дополнительные сведения см. в статье [Шифрование резервной копии](../relational-databases/backup-restore/backup-encryption.md).  
  
  
###  <a name="CE"></a>Новый дизайн для оценки количества элементов  
 Логика оценки количества элементов, называемая механизмом оценки количества элементов, переработана в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] в целях улучшения качества планов запросов и тем самым повышения производительности запросов. Новый механизм оценки количества элементов состоит из предположений и алгоритмов, которые отлично подходят для современных рабочих нагрузок OLTP и хранилища данных. Он основан на глубоком исследовании оценки количества элементов для современных рабочих нагрузок и нашем опыте усовершенствования этого механизма, накопленном за последние 15 лет. Отзывы от клиентов свидетельствуют, что эти изменения положительно сказываются на большинстве запросов либо все остается по прежнему, хотя производительность небольшого числа запросов может снизиться по сравнению с использованием предыдущего механизма оценки количества элементов. Рекомендации по настройке и тестированию производительности см. в разделе [Оценка количества элементов &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md).  
   
  
###  <a name="Durability"></a>Отложенная устойчивость  
 В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] добавляется возможность сократить задержку путем назначения некоторых или всех транзакций отложенными устойчивыми. Отложенная долговечная транзакция передает управление клиенту перед фиксацией записи журнала транзакций на диск. Устойчивостью можно управлять на уровне базы данных, COMMIT или блоков ATOMIC.  
  
 Дополнительные сведения см. в разделе [Управление устойчивостью транзакций](../relational-databases/logs/control-transaction-durability.md).  
  
  
###  <a name="AlwaysOn"></a>Усовершенствования AlwaysOn  
 
  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] содержит следующие усовершенствования для экземпляров отказоустойчивого кластера AlwaysOn и групп доступности AlwaysOn:  
  
-   Мастер добавления реплики Azure упрощает создание гибридных решений для групп доступности AlwaysOn. Дополнительные сведения см. [в статье Использование мастера добавления реплики Azure &#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md).  
  
-   Максимальное число вторичных реплик увеличено с 4 до 8.  
  
-   Теперь после разрыва соединения с первичной репликой или в период отсутствия кворума кластера предназначенные для чтения вторичные реплики остаются доступными для рабочих нагрузок операций чтения.  
  
-   Теперь в экземплярах отказоустойчивого кластера (FCI) могут использоваться общие тома кластера как общие диски кластера. Дополнительные сведения см. в разделе [Always on экземпляры отказоустойчивого кластера](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
-   Доступна новая системная функция [sys.fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql)и новое динамическое административное представление [sys.dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql).  
  
-   Следующие динамические административные представления были улучшены и теперь возвращают данные FCI: [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)и [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql).  
  
  
###  <a name="OIR"></a>Переключение секций и индексирование  
 Теперь отдельные секции секционированных таблиц можно перестраивать. Дополнительные сведения см. в разделе [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Lock"></a>Управление приоритетом блокировки операций в сети  
 Параметр `ONLINE = ON` теперь содержит параметр `WAIT_AT_LOW_PRIORITY`, который позволяет указывать, как долго в процессе перестроения должно происходить ожидание необходимых блокировок. Кроме того, параметр `WAIT_AT_LOW_PRIORITY` позволяет настраивать завершение процессов блокировки, связанных с инструкцией перестроения. Дополнительные сведения см. в разделах [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) и [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql). Сведения об устранении новых типов состояний блокировки доступны в [sys. dm_tran_locks &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) и [sys. dm_os_wait_stats &#40;transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
 
  
###  <a name="CCI"></a>Индексы columnstore  
 Эти новые возможности доступны для индексов columnstore:  
  
-   **Кластеризованные индексы Columnstore**  
  
     Кластеризованный индекс columnstore позволяет повысить производительность запросов и сжатие данных для рабочих нагрузок хранилища данных, которые, в основном, выполняют массовую загрузку и запросы только для чтения. Поскольку кластеризованный индекс columnstore может обновляться, рабочая нагрузка может также выполнять несколько операций вставки, обновления и удаления. Дополнительные сведения см. в разделе [Описание индексов columnstore](../relational-databases/indexes/columnstore-indexes-described.md) и [Использование кластеризованных индексов columnstore](../relational-databases/indexes/indexes.md).  
  
-   **SHOWPLAN**  
  
     Инструкция SHOWPLAN отображает сведения об индексах columnstore. Свойства **EstimatedExecutionMode** и **ActualExecutionMode** имеют два возможных значения: **Batch** и **Row**.  Свойство **Storage** имеет два возможных значения: **RowStore** и **ColumnStore**.  
  
-   **Сжатие архивных данных**  
  
     ИЗМЕНИТЬ ИНДЕКС... Перестроение имеет новый параметр сжатия данных COLUMNSTORE_ARCHIVE, который дополнительно сжимает указанные секции индекса COLUMNSTORE. Это может использоваться для архивации или в других ситуациях, где требуется уменьшение размера хранилища данных и допускается увеличение затрат времени на сохранение и выборку. Дополнительные сведения см. в разделе [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
   
  
###  <a name="Buffer"></a>Расширение буферного пула  
 Параметр [Расширение буферного пула](configure-windows/buffer-pool-extension.md) обеспечивает безукоризненную интеграцию твердотельных накопителей (SSD) в качестве расширения энергонезависимого ОЗУ (NvRAM) для буферного пула компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , что способствует значительному повышению пропускной способности ввода-вывода.  
   
  
###  <a name="Stats"></a>Добавочная статистика  
 CREATE STATISTICS и связанные статистические инструкции теперь позволяют создавать статистики по отдельным секциям с параметром INCREMENTAL. Соответствующие инструкции позволяют использовать добавочные статистики или формируют отчет по ним. Затронутый синтаксис включает обновление статистики, sp_createstats, создание ИНДЕКСов, изменение индекса, параметры ALTER DATABASE SET, DATABASEPROPERTYEX, sys. databases и sys. stats. Дополнительные сведения см. в разделе [CREATE STATISTICS &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-statistics-transact-sql).  
  
  
###  <a name="RG"></a>Resource Governor улучшений для управления физическими операциями ввода-вывода  
 Регулятор ресурсов позволяет задать ограничения на загрузку ЦП, физических средств ввода-вывода и использование памяти, которые доступны для входящих запросов приложений в пуле ресурсов. В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]можно использовать новый MIN_IOPS_PER_VOLUME и параметры MAX_IOPS_PER_VOLUME для управления физических операций ввода-вывода, выданные потоков для пользователя для данного пула ресурсов. Дополнительные сведения см. в статьях [Resource Governor пул ресурсов](../relational-databases/resource-governor/resource-governor-resource-pool.md) и [создание пула ресурсов &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 Параметр MAX_OUTSTANDING_IO_PER_VOLUME ALTER RESOURCE GOVENOR устанавливает максимальное количество необработанных операций дискового ввода-вывода на том. С помощью этого параметра выполняется настройка управления ресурсами ввода-вывода в соответствии с характеристиками ввода-вывода тома диска. Он также может использоваться для ограничения количества операций ввода-вывода на границе экземпляра SQL Server. Дополнительные сведения см. в разделе [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql).  
  
  
###  <a name="OnlineEvent"></a>Класс событий Online Index Operation  
 Отчет о состоянии для класса событий «операции с индексами в сети» теперь содержит 2 новых столбца данных: **идентификатор_секции** и **номер_секции**. Дополнительные сведения см. в разделе [Progress Report: Online Index Operation Event Class](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md).  
  
  
###  <a name="Compat"></a>Уровень совместимости базы данных  
 Уровень совместимости 90 не является допустимым в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]. Дополнительные сведения см. в статье [уровень совместимости ALTER database &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) .  
  
##  <a name="TSQL"></a>Улучшения Transact-SQL  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>Встроенная спецификация CLUSTERED и NONCLUSTERED  
 Теперь для таблиц, находящихся на диске, применима встроенная спецификация индексов `CLUSTERED` и `NONCLUSTERED`. Создание таблицы со встроенными индексами эквивалентно выполнению инструкции создания таблицы, за которой следуют соответствующие инструкции `CREATE INDEX`. Для таблиц со встроенными индексами не поддерживаются включенные столбцы и условия фильтра.  
  
### <a name="select--into"></a>ВЫБЕРИТЕ... БИТЬ  
 Инструкция `SELECT ... INTO` усовершенствована и теперь может быть выполнена параллельно. Уровню совместимости базы данных должно быть присвоено значение не менее 110.  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>Улучшения [!INCLUDE[tsql](../includes/tsql-md.md)] для In-Memory OLTP  
 Дополнительные сведения об изменениях [!INCLUDE[tsql](../includes/tsql-md.md)] для поддержки In-Memory OLTP см. в разделе [Transact-SQL Support for In-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md).  
  
  
##  <a name="SystemTable"></a>Улучшения системного представления  
  
### <a name="sysxml_indexes"></a>sys.xml_indexes  
 [sys. xml_indexes &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql) имеют три новых столбца: `xml_index_type`, `xml_index_type_description`и `path_id`.  
  
### <a name="sysdm_exec_query_profiles"></a>sys.dm_exec_query_profiles  
 [sys. dm_exec_query_profiles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql) наблюдает за ходом выполнения запросов в режиме реального времени во время выполнения запроса.  
  
### <a name="syscolumn_store_row_groups"></a>sys.column_store_row_groups  
 [sys. column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql) предоставляет сведения о кластеризованном индексе columnstore для каждого сегмента, чтобы помочь администратору принять решения по управлению системой.  
  
### <a name="sysdatabases"></a>sys.databases  
 [sys. databases &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) содержит три новых столбца `is_auto_create_stats_incremental_on`: `is_query_store_on`, и `resource_pool_id`.  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>Улучшения системного представления для In-Memory OLTP  
 Сведения об улучшениях системного представления для поддержки OLTP в памяти см. в разделе [системные представления, хранимые процедуры, динамические административные представления и типы ожидания для выполняющейся в памяти OLTP](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).  
   
  
##  <a name="Security"></a>Улучшения безопасности  
  
### <a name="connect-any-database-permission"></a>Разрешение CONNECT ANY DATABASE  
 Новое разрешение на уровне сервера. Предоставьте разрешение **CONNECT ANY DATABASE** имени входа, которому нужно подключиться ко всем существующим базам данных и ко всем новым базам, которые могут быть созданы в будущем. Не предоставляет каких-либо разрешений в базах данных за пределами соединения. Используйте сочетание с **любыми защищаемыми объектами пользователя** или `VIEW SERVER STATE` , чтобы разрешить процессу аудита просматривать все данные или все состояния базы данных на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="impersonate-any-login-permission"></a>Разрешение IMPERSONATE ANY LOGIN  
 Новое разрешение на уровне сервера. После предоставления разрешает процессу среднего уровня олицетворять учетную запись клиентов, подключающихся к ней, так как она подключается к базам данных. При запрещении имени входа с высоким уровнем прав может быть запрещено олицетворение других имен входа. Например, имени входа с разрешением **CONTROL SERVER** можно запретить олицетворение других имен входа.  
  
### <a name="select-all-user-securables-permission"></a>Разрешение SELECT ALL USER SECURABLES  
 Новое разрешение на уровне сервера. После предоставления имя входа, например аудитор, сможет просматривать данные во всех базах данных, к которым может подключаться пользователь.  
  
  
##  <a name="Deployment"></a>Усовершенствования развертывания  
### <a name="azure-vm"></a>Azure
[Развертывание базы данных SQL Server на виртуальной машине Microsoft Azure позволяет развернуть](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] базу данных на виртуальной машине Azure.  

### <a name="refs"></a>ReFS
Теперь поддерживается развертывание баз данных в ReFS.   
  
## <a name="see-also"></a>См. также:  
 [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
