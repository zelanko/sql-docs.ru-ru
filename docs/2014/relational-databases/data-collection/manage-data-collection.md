---
title: Управление сбором данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 543f972f5c5805bb1508b6a256f7a7ed3a2aaa3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62918596"
---
# <a name="manage-data-collection"></a>Управление сбором данных
  Хранимые процедуры и функции среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] могут быть использованы для управления различными аспектами сбора данных (например, включать или отключать сбор данных, изменять конфигурацию набора сбора или просматривать данные в хранилище данных управления).  
  
## <a name="manage-data-collection-by-using-sql-server-management-studio"></a>Управление сбором данных с использованием среды SQL Server Management Studio  
 Следующие задачи, связанные со сборщиком данных, вы можете выполнять с помощью обозревателя объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   [Настройка SQL Server Management Studio &#40;хранилища управляющих данных&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [Настройка свойств сборщика данных](configure-properties-of-a-data-collector.md)  
  
-   [Включение или отключение сбор данных](data-collection.md)  
  
-   [Запуск или остановка набора элементов сбора](start-or-stop-a-collection-set.md)  
  
-   [Используйте SQL Server Profiler, чтобы создать набор элементов сбора трассировки SQL &#40;SQL Server Management Studio&#41;](use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [Просмотр журналов набора элементов сбора &#40;SQL Server Management Studio&#41;](view-collection-set-logs-sql-server-management-studio.md)  
  
-   [Просмотр или изменение расписаний наборов элементов сбора &#40;SQL Server Management Studio&#41;](view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [Просмотр SQL Server Management Studio &#40;отчетов набора сбора&#41;](view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-by-using-transact-sql"></a>Управление сбором данных с помощью языка Transact-SQL  
 Сборщик данных располагает большим набором хранимых процедур, который помогает выполнить любую задачу сборщика данных. Например, [!INCLUDE[tsql](../../includes/tsql-md.md)]позволяет выполнять следующие задачи.  
  
-   [Настройка параметров сбора данных &#40;&#41;Transact-SQL](configure-data-collection-parameters-transact-sql.md)  
  
-   [Включение или отключение сбор данных](data-collection.md)  
  
-   [Запуск или остановка набора элементов сбора](start-or-stop-a-collection-set.md)  
  
-   [Создание пользовательского набора сбора, использующего тип сборщика «Универсальный запрос T-SQL» &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [Добавление элемента сбора в набор элементов сбора &#40;&#41;Transact-SQL](add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 Кроме того, предусмотрены функции и представления, использующиеся для получения данных конфигурации для базы данных msdb и хранилища данных управления, данных журнала выполнения и данных, записанных в хранилище данных управления.  
  
 Существующие хранимые процедуры, функции и представления позволяют создавать собственные комплексные сценарии сбора данных.  
  
> [!IMPORTANT]  
>  В отличие от обычных хранимых процедур, в хранимых процедурах сборщика данных используются жестко типизированные параметры и не поддерживается автоматическое преобразование типов данных. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
 С помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно создавать и выполнять представленные образцы кода. Дополнительные сведения см. в статье [Семантический поиск](../../ssms/object/object-explorer.md). В качестве альтернативы можно создать запрос в любом редакторе и сохранить его в текстовом файле с расширением SQL. Выполнить запрос из командной строки Windows можно с помощью программы `sqlcmd`. Дополнительные сведения см. [в разделе Использование служебной программы sqlcmd](../scripting/sqlcmd-use-the-utility.md).  
  
### <a name="stored-procedures-and-views"></a>Хранимые процедуры и представления  
 **Работа с сборщиком данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе со сборщиком данных.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)|Включить сборщик данных.|  
|[sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)|Выключить сборщик данных.|  
  
 **Работа с наборами сбора**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с наборами сбора.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_run_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql)|Запускает набор сбора по запросу.|  
|[sp_syscollector_start_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql)|Запуск набора сбора.|  
|[sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql)|Остановка набора сбора.|  
|[sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql)|Создание набора сбора.|  
|[sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql)|Удаление набора сбора.|  
|[sp_syscollector_update_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql)|Изменение конфигурации набора сбора.|  
|[sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql)|Передача данных набора сбора в хранилище управляющих данных. Фактически передача производится по требованию.|  
  
 **Работа с элементами сбора**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с элементами сбора.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql)|Создание элемента коллекции.|  
|[sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql)|Удаление элемента коллекции.|  
|[sp_syscollector_update_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql)|Обновление элемента коллекции.|  
  
 **Работа с типами сборщиков**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с типами сборщиков.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql)|Создание типа сборщика.|  
|[sp_syscollector_update_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql)|Обновление типа сборщика.|  
|[sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql)|Удаление типа сборщика.|  
  
 **Получение сведений о конфигурации**  
  
 В следующей таблице описаны представления, используемые для получения сведений о конфигурации и данных журнала выполнения.  
  
|Имя представления|Description|  
|---------------|-----------------|  
|[syscollector_config_store &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-config-store-transact-sql)|Получение конфигурации сборщика данных.|  
|[syscollector_collection_items &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-items-transact-sql)|Получение сведений об элементе коллекции.|  
|[syscollector_collection_sets &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql)|Получение сведений о наборе сбора.|  
|[syscollector_collector_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collector-types-transact-sql)|Получение сведений о типе сборщика.|  
|[syscollector_execution_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-transact-sql)|Получение сведений о выполнении набора сбора и пакета.|  
|[syscollector_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql)|Получение сведений о выполнении задачи.|  
|[syscollector_execution_log_full &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql)|Получение сведений о том, когда журнал выполнения заполнится.|  
  
 **Настройка доступа к хранилищу данных управления**  
  
 В следующей таблице описаны хранимые процедуры, используемые для настройки доступа к хранилищу данных управления.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql)|Укажите имя базы данных, определенное в строке соединения с хранилищем управляющих данных.|  
|[sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql)|Укажите экземпляр, определенный в строке соединения с хранилищем управляющих данных.|  
  
 **Настройка хранилища управляющих данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с конфигурацией хранилища данных управления.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[ядро. sp_create_snapshot &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql)|Создание моментального снимка сбора в хранилище управляющих данных.|  
|[ядро. sp_update_data_source &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql)|Обновление источника данных для сбора данных.|  
|[ядро. sp_add_collector_type &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql)|Добавление типа сборщика в хранилище управляющих данных.|  
|[ядро. sp_remove_collector_type &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql)|Удаление типа сборщика из хранилища управляющих данных.|  
|[ядро. sp_purge_data &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql)|Удаление данных из хранилища данных управления.|  
  
 **Работа с пакетами отправки**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с пакетами передачи.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql)|Настройка количества попыток передачи данных.|  
|[sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql)|Указание временного хранилища данных между попытками передачи.|  
  
 **Работа с журналом выполнения сбора данных**  
  
 В следующей таблице описаны хранимые процедуры, используемые при работе с журналом выполнения сбора данных.  
  
|Имя процедуры|Description|  
|--------------------|-----------------|  
|[sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql)|Удаление записей о наборах сбора из журнала выполнения.|  
  
### <a name="functions"></a>Функции  
 В следующей таблице описаны функции, используемые для получения сведений о выполнении и трассировке.  
  
|Имя функции|Description|  
|-------------------|-----------------|  
|[fn_syscollector_get_execution_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql)|Получение данных журнала выполнения служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] для определенного пакета.|  
|[fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql)|Получение статистики выполнения для пакета или набора сбора. Эти сведения включают записанные в журнал ошибки.|  
|[моментальные снимки. fn_trace_getdata &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql)|Получение событий, записанных в журнал при использовании типа сборщика «Универсальная трассировка SQL».|  
  
## <a name="see-also"></a>См. также:  
 [Выполнение хранимой процедуры](../stored-procedures/execute-a-stored-procedure.md)   
 [Использование SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)   
 [Сбор данных](data-collection.md)  
  
  
