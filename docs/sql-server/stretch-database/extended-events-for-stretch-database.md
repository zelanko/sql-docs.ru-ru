---
title: Расширенные события для Stretch Database | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 70485e74-2e25-4e7e-be6c-9dd1780a42e3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0b778ab0bad4b86276114bb943b36cf78a7a2d73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666012"
---
# <a name="extended-events-for-stretch-database"></a>Расширенные события для Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


База данных Stretch предоставляет набор расширенных событий для поиска и устранения неполадок.  
  
Дополнительные сведения см. в статье [Расширенные события](../../relational-databases/extended-events/extended-events.md). Сведения о запуске сеанса расширенных событий для поиска и устранения неполадок см. в статье [Создание сеанса расширенных событий](http://msdn.microsoft.com/library/34b1e95a-a80e-4aca-9201-abde47f2ca74).  
  
## <a name="list-of-extended-events-for-stretch-database"></a>Список расширенных событий для базы данных Stretch  
  
Имя события|Описание события   
---------|---------  
remote_data_archive_db_ddl|Происходит при обработке базы данных языка DDL T-SQL для расширения данных.  
remote_data_archive_provision_operation|Возникает при начале или окончании операции подготовки.  
remote_data_archive_query_rewrite|Возникает, когда RelOp_Get заменяется при перезаписи запроса растяжения.  
remote_data_archive_table_ddl|Происходит при обработке языка DDL T-SQL для расширения данных.  
remote_data_archive_telemetry|Возникает, когда локальная система передает событие телеметрии на Azure DB.  
remote_data_archive_telemetry_rejected|Возникает при отклонении события телеметрии AzureDB Stretch.  
repopulate_stretch_schema_task_queue_complete|Передает данные о завершении повторного заполнения очереди задач растягивания схемы.  
repopulate_stretch_schema_task_queue_start|Передает данные о начале повторного заполнения очереди задач растягивания схемы.  
stretch_codegen_errorlog|Сообщает выходные данные генератора кода.  
stretch_codegen_start|Сообщает о начале создания кода расширения.  
stretch_create_remote_table_start|Сообщает о начале создания удаленной таблицы.  
stretch_database_disable_completed|Сообщает о выполнении команды ALTER DATABASE SET REMOTE_DATA_ARCHIVE OFF.  
stretch_database_enable_completed|Сообщает о выполнении команды ALTER DATABASE SET REMOTE_DATA_ARCHIVE ON.  
stretch_database_reauthorize_completed|Сообщает о завершении специальной процедуры sp_rda_reauthorize_db.  
stretch_index_reconciliation_codegen_completed|Сообщает о завершении создания кода для операции растягивания удаленного индекса.  
stretch_index_update_step_completed|Сообщает длительность операции обновления растянутого индекса.  
stretch_migration_debug_trace|Трассировка отладки действий растянутого переноса.  
stretch_migration_dequeue_migration|Событие, создаваемое, когда пакет задач растяжения миграции удален из очереди для базы данных.  
stretch_migration_queue_migration|Постановка пакета в очередь для начала переноса базы данных и объекта.  
stretch_migration_requeue_migration|Событие, создаваемое, когда пакет задач растяжения миграции повторно поставлен в очередь.  
stretch_migration_start_migration|Запуск переноса базы данных и объекта.  
stretch_migration_start_unmigration|Запуск отмены миграции базы данных и объекта.  
stretch_remote_column_execution_completed|Сообщает о завершении удаленного выполнения для сформированного кода растянутого столбца.  
stretch_remote_column_reconciliation_codegen_completed|Сообщает, что создание кода для сверки растянутых удаленных столбцов завершено.  
stretch_remote_index_execution_completed|Сообщает о завершении удаленного выполнения для созданного кода растянутого индекса.  
stretch_schema_queue_task|Сообщает, когда пакет будет поставлен в очередь для обработки задачи схемы для базы данных и объекта.  
stretch_schema_script_execution_completed|Передает данные о завершении выполнения скрипта растягивания во время обработки задачи растягивания схемы.  
stretch_schema_script_execution_skipped|Передает данные о пропуске выполнения скрипта растягивания во время обработки задачи растягивания схемы.  
stretch_schema_script_execution_start|Передает данные о начале выполнения скрипта растягивания во время обработки задачи растягивания схемы.  
stretch_schema_task_failed|Передает данные о сбое функции растягивания схемы во время задачи растягивания схемы.  
stretch_schema_task_skipped|Сообщает, что задача растянутой схемы при выполнении функции растянутой схемы была пропущена.  
stretch_schema_task_start|Сообщает о запуске функции растянутой схемы во время задачи растягивания схемы.  
stretch_schema_task_succeeded|Передает данные об успешном завершении функции растягивания схемы во время задачи растягивания схемы.  
stretch_sp_migration_get_batch_id|Вызов sp_stretch_get_batch_id.  
stretch_sync_metadata_start|Сообщает о начале проверок метаданных во время выполнения перемещения.  
stretch_table_codegen_completed|Сообщает о завершении создания кода для расширенной таблицы.  
stretch_table_complete_data_reconciliation|Завершить сверку данных между базой данных и объектом.  
stretch_table_data_reconciliation_event|Сообщает о завершении сверки данных в пакете строк.  
stretch_table_data_reconciliation_results_event|Сообщает об ошибке или успешном завершении сверки данных между несколькими пакетами строк.  
stretch_table_hinted_admin_delete_event|Сообщает о выполнении операции DML растянутого обновления, в которой использовалась подсказка администратора.  
stretch_table_hinted_admin_update_event|Сообщает о выполнении операции DML растянутого обновления, в которой использовалась подсказка администратора.  
stretch_table_provisioning_step_completed|Сообщает длительность операции подготовки расширенной таблицы.  
stretch_table_query_error|Сообщает об ошибке, возникшей во время перезаписи запроса на растяжение.  
stretch_table_remote_creation_completed|Сообщает о завершении удаленного выполнения созданного кода для расширенной таблицы.  
stretch_table_row_migration_event|Сообщает о завершении перемещения пакета строк.  
stretch_table_row_migration_results_event|Сообщает об ошибке или успешном завершении перемещения нескольких пакетов строк.  
stretch_table_row_unmigration_event|Сообщает о завершении отмены перемещения пакета строк.  
stretch_table_row_unmigration_results_event|Сообщает об ошибке или успешной отмене миграции нескольких пакетов строк.  
stretch_table_start_data_reconciliation|Начать сверку данных между базой данных и объектом.  
stretch_table_unprovision_completed|Сообщает о завершении удаления локальных ресурсов для таблицы, для которой было отменено расширение.  
stretch_table_validation_error|Сообщает о завершении проверки таблицы, когда пользователь включает расширение.  
stretch_unprovision_table_start|Сообщает о начале отмены подготовки таблицы расширения.  
  
## <a name="see-also"></a>См. также:  
[Управление Stretch Database и устранение связанных с ней неполадок](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)  

