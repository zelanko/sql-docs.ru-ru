---
title: Управление сбором данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- Сбор данных
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2405449dad69e386aa267f683c672533b3c02276
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40405570"
---
# <a name="manage-data-collection"></a>Управление сбором данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
 Хранимые процедуры и функции среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] могут быть использованы для управления различными аспектами сбора данных (например, включать или отключать сбор данных, изменять конфигурацию набора сбора или просматривать данные в хранилище данных управления).  
  
## <a name="manage-data-collection-using-ssms"></a>Управление сбором данных с помощью SSMS  
 Следующие задачи, связанные со сборщиком данных, выполняются с помощью обозревателя объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   [Настройка хранилища данных управления (среда SQL Server Management Studio)](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [Настройка свойств сборщика данных](../../relational-databases/data-collection/configure-properties-of-a-data-collector.md)  
  
-   [Включение или отключение сбор данных](../../relational-databases/data-collection/enable-or-disable-data-collection.md)  
  
-   [Запуск или остановка набора элементов сбора](../../relational-databases/data-collection/start-or-stop-a-collection-set.md)  
  
-   [Использование приложения SQL Server Profiler для создания набора элементов сбора трассировки SQL (среда SQL Server Management Studio)](../../relational-databases/data-collection/use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [Просмотр журналов набора элементов сбора (среда SQL Server Management Studio)](../../relational-databases/data-collection/view-collection-set-logs-sql-server-management-studio.md)  
  
-   [Просмотр и изменение расписаний набора элементов сбора (среда SQL Server Management Studio)](../../relational-databases/data-collection/view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [Просмотр отчета о наборе элементов сбора (среда SQL Server Management Studio)](../../relational-databases/data-collection/view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-using-transact-sql"></a>Управление сбором данных с помощью языка Transact-SQL  
 Сборщик данных располагает большим набором хранимых процедур, который помогает выполнить любую задачу сборщика данных. Например, [!INCLUDE[tsql](../../includes/tsql-md.md)]позволяет выполнять следующие задачи.  
  
-   [Настройка параметров сбора данных (Transact-SQL)](../../relational-databases/data-collection/configure-data-collection-parameters-transact-sql.md)  
  
-   [Включение или отключение сбор данных](../../relational-databases/data-collection/enable-or-disable-data-collection.md)  
  
-   [Запуск или остановка набора элементов сбора](../../relational-databases/data-collection/start-or-stop-a-collection-set.md)  
  
-   [Создание пользовательского набора элементов сбора, использующего тип сборщика "Универсальный запрос T-SQL" (Transact-SQL)](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [Добавление элемента сбора в набор элементов сбора (Transact-SQL)](../../relational-databases/data-collection/add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 Кроме того, предусмотрены функции и представления, использующиеся для получения данных конфигурации для базы данных msdb и хранилища данных управления, данных журнала выполнения и данных, записанных в хранилище данных управления.  
  
 Существующие хранимые процедуры, функции и представления позволяют создавать собственные комплексные сценарии сбора данных.  
  
>**ВАЖНО!** В отличие от обычных хранимых процедур, в хранимых процедурах сборщика данных используются жестко типизированные параметры и не поддерживается автоматическое преобразование типов данных. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет создавать и выполнять представленные образцы кода. Дополнительные сведения см. в статье [Семантический поиск](../../ssms/object/object-explorer.md). В качестве альтернативы можно создать запрос в любом редакторе и сохранить его в текстовом файле с расширением SQL. Выполнить запрос из командной строки Windows можно с помощью программы **sqlcmd** . Дополнительные сведения см. в статье [Программа sqlcmd](../../relational-databases/scripting/sqlcmd-use-the-utility.md).  
  
### <a name="stored-procedures-and-views"></a>Хранимые процедуры и представления  
 **Работа со сборщиком данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе со сборщиком данных.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md)|Включить сборщик данных.|  
|[sp_syscollector_disable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql.md)|Выключить сборщик данных.|  
  
 **Работа с наборами сбора**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с наборами сбора.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_run_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql.md)|Запускает набор сбора по запросу.|  
|[sp_syscollector_start_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql.md)|Запуск набора сбора.|  
|[sp_syscollector_stop_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md)|Остановка набора сбора.|  
|[sp_syscollector_create_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)|Создание набора сбора.|  
|[sp_syscollector_delete_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql.md)|Удаление набора сбора.|  
|[sp_syscollector_update_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql.md)|Изменение конфигурации набора сбора.|  
|[sp_syscollector_upload_collection_set (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql.md)|Передача данных набора сбора в хранилище управляющих данных. Фактически передача производится по требованию.|  
  
 **Работа с элементами коллекции**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с элементами сбора.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_create_collection_item (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)|Создание элемента коллекции.|  
|[sp_syscollector_delete_collection_item (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql.md)|Удаление элемента коллекции.|  
|[sp_syscollector_update_collection_item (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql.md)|Обновление элемента коллекции.|  
  
 **Работа с типами сборщика**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с типами сборщиков.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_create_collector_type (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql.md)|Создание типа сборщика.|  
|[sp_syscollector_update_collector_type (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql.md)|Обновление типа сборщика.|  
|[sp_syscollector_delete_collector_type (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql.md)|Удаление типа сборщика.|  
  
 **Получение сведений о конфигурации**  
  
 В следующей таблице описаны представления, используемые для получения сведений о конфигурации и данных журнала выполнения.  
  
|Имя представления|Описание|  
|---------------|-----------------|  
|[syscollector_config_store (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)|Получение конфигурации сборщика данных.|  
|[syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)|Получение сведений об элементе коллекции.|  
|[syscollector_collection_sets (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)|Получение сведений о наборе сбора.|  
|[syscollector_collector_types (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)|Получение сведений о типе сборщика.|  
|[syscollector_execution_log (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)|Получение сведений о выполнении набора сбора и пакета.|  
|[syscollector_execution_stats (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)|Получение сведений о выполнении задачи.|  
|[syscollector_execution_log_full (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)|Получение сведений о том, когда журнал выполнения заполнится.|  
  
 **Настройка доступа к хранилищу управляющих данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые для настройки доступа к хранилищу данных управления.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_set_warehouse_database_name (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql.md)|Укажите имя базы данных, определенное в строке соединения с хранилищем управляющих данных.|  
|[sp_syscollector_set_warehouse_instance_name (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql.md)|Укажите экземпляр, определенный в строке соединения с хранилищем управляющих данных.|  
  
 **Настройка хранилища управляющих данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с конфигурацией хранилища данных управления.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[core.sp_create_snapshot (Transact-SQL)](../../relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql.md)|Создание моментального снимка сбора в хранилище управляющих данных.|  
|[core.sp_update_data_source (Transact-SQL)](../../relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql.md)|Обновление источника данных для сбора данных.|  
|[core.sp_add_collector_type (Transact-SQL)](../../relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql.md)|Добавление типа сборщика в хранилище управляющих данных.|  
|[core.sp_remove_collector_type (Transact-SQL)](../../relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql.md)|Удаление типа сборщика из хранилища управляющих данных.|  
|[core.sp_purge_data (Transact-SQL)](../../relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql.md)|Удаление данных из хранилища данных управления.|  
  
 **Работа с пакетами передачи**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с пакетами передачи.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_set_cache_window (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)|Настройка количества попыток передачи данных.|  
|[sp_syscollector_set_cache_directory (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql.md)|Указание временного хранилища данных между попытками передачи.|  
  
 **Работа с журналом выполнения сбора данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с журналом выполнения сбора данных.  
  
|Имя процедуры|Описание|  
|--------------------|-----------------|  
|[sp_syscollector_delete_execution_log_tree (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql.md)|Удаление записей о наборах сбора из журнала выполнения.|  
  
### <a name="functions"></a>Функции  
 В следующей таблице описаны функции, используемые для получения сведений о выполнении и трассировке.  
  
|Имя функции|Описание|  
|-------------------|-----------------|  
|[fn_syscollector_get_execution_details (Transact-SQL)](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md)|Получение данных журнала выполнения служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] для определенного пакета.|  
|[fn_syscollector_get_execution_stats (Transact-SQL)](../../relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql.md)|Получение статистики выполнения для пакета или набора сбора. Эти сведения включают записанные в журнал ошибки.|  
|[snapshots.fn_trace_getdata (Transact-SQL)](../../relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql.md)|Получение событий, записанных в журнал при использовании типа сборщика «Универсальная трассировка SQL».|  
  
## <a name="see-also"></a>См. также раздел  
 [Выполнение хранимой процедуры](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)   
 [Использование среды SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
