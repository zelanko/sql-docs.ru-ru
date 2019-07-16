---
title: sys.dm_user_db_resource_governance (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governance
- sys.resource_governance_TSQL
- resource_governance
- resource_governance_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governance catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: eebc22fa4f17680b843f195777d7cc5f4b2835ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090452"
---
# <a name="sysdmuserdbresourcegovernance-transact-sql"></a>sys.dm_user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Возвращает параметры конфигурации и емкости для базы данных базы данных SQL Azure управление ресурсами.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|ssNoversion|Идентификатор базы данных, уникальное в пределах сервера базы данных SQL Azure.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Логический идентификатор guid для пользовательской базы данных и остается на протяжении жизненного цикла пользовательской базы данных.  Переименование или перевод базы данных на другой цели уровня Обслуживания не приведет к изменению идентификатор GUID. |
|**physical_database_guid**|UNIQUEIDENTIFIER|Guid физического для пользовательской базы данных, который остается на протяжении жизненного цикла физического экземпляра базы данных пользователей. Параметр, чтобы разные цели уровня Обслуживания вызовет этот столбец для изменения.|
|**server_name**|nvarchar|Имя логического сервера.|
|**database_name**|nvarchar|Имя логической базы данных.|
|**slo_name**|nvarchar|Служба цели Создание и на уровне оборудования.|
|**dtu_limit**|ssNoversion|Лимит DTU базы данных (NULL для виртуальное).|
|**cpu_limit**|ssNoversion|Виртуальное ядро предел (NULL для баз данных DTU) базы данных.|
|**min_cpu**|tinyint|Минимальный процент ЦП, который может использоваться пользователем рабочей нагрузкой.|
|**max_cpu**|tinyint|Максимальный процент ЦП, который может использоваться пользователем рабочей нагрузкой.|
|**cap_cpu**|tinyint|Ограничение процентов ЦП для группы рабочей нагрузки пользователей.|
|**min_cores**|smallint|Количество процессоров, используемых SQL.|
|**max_dop**|smallint|Максимальная степень параллелизма, используемых рабочую нагрузку для пользователя.|
|**min_memory**|ssNoversion|Процент минимальный объем памяти, могут использоваться рабочую нагрузку для пользователя.|
|**MAX_MEMORY**|ssNoversion|Процент максимального объема памяти, могут использоваться рабочую нагрузку для пользователя.|
|**max_sessions**|ssNoversion|Ограничение сеансов для группы пользователей.|
|**max_memory_grant**|ssNoversion|Максимальный объем памяти предоставить для каждого запроса в рабочую нагрузку для пользователя в процентах.|
|**max_db_memory**|ssNoversion|Max предельного значения памяти буферного пула для рабочей нагрузке базы данных пользователя|
|**govern_background_io**|bit|Указывает, оплачиваются ли операции записи в фоновом режиме для группы пользователей.|
|**min_db_max_size_in_mb**|BIGINT|Размер файла базы данных с минимальным Max в МБ.|
|**max_db_max_size_in_mb**|BIGINT|Максимальное Max файл базы данных, в МБ.|
|**default_db_max_size_in_mb**|BIGINT|По умолчанию максимальный размер базы данных файл, в МБ.|
|**db_file_growth_in_mb**|BIGINT|По умолчанию размером файла базы данных azure, в МБ.|
|**initial_db_file_size_in_mb**|BIGINT|По умолчанию базы данных размер файла в МБ.|
|**log_size_in_mb**|BIGINT|По умолчанию размер файла журнала в МБ.|
|**instance_cap_cpu**|ssNoversion|Ограничение ЦП на уровне экземпляра.|
|**instance_max_log_rate**|BIGINT|Версия журнала cap скорость на уровне экземпляра, в байтах в секунду.|
|**instance_max_worker_threads**|ssNoversion|Предел рабочих потоков на уровне экземпляра.|
|**replica_type**|ssNoversion|Тип репликации, где 0 является первичной, а 1 — дополнительный.|
|**max_transaction_size**|BIGINT|Максимальный объем журнала, любая транзакция, в КБ.|
|**checkpoint_rate_mbps**|ssNoversion|Контрольная точка полоса пропускания, Мбит/с.|
|**checkpoint_rate_io**|ssNoversion|Частота установки контрольных точек операции ввода-ВЫВОДА в операций ввода-вывода в секунду.|
|**last_updated_date_utc**|datetime|Дата и время последнего изменения настроек или перенастройки.|
|**primary_group_id**|ssNoversion|Идентификатор группы рабочей нагрузки основного пользователя.|
|**primary_group_max_workers**|ssNoversion|Количества работников на уровне группы рабочей нагрузки основного пользователя.|
|**primary_min_log_rate**|BIGINT|Скорость минимальное журнала (байт / с) на уровне группы рабочей нагрузки основного пользователя.|
|**primary_max_log_rate**|BIGINT|Скорость максимальное журнала (байт / с) на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_min_io**|ssNoversion|Минимальное операций ввода-ВЫВОДА на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_max_io**|ssNoversion|Максимальное операций ввода-ВЫВОДА на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_min_cpu**|float|Минимальный процент ЦП ограничить на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_max_cpu**|float|Максимальный процент ограничения на ЦП на уровне группы рабочей нагрузки основного пользователя.|
|**primary_log_commit_fee**|ssNoversion|Журнал управления фиксации тариф на уровне группы рабочей нагрузки основного пользователя.|
|**primary_pool_max_workers**|ssNoversion|Количества работников на уровне пула основного пользователя.
|**pool_max_io**|ssNoversion|Максимальное ограничение ввода-ВЫВОДА на уровне пула основного пользователя.|
|**govern_db_memory_in_resource_pool**|bit|Указывает, действует ли максимальный размер буферного пула на уровне пула ресурсов. Обычно задается для баз данных в эластичных пулах.|
|**volume_local_iops**|ssNoversion|-Вывода на второй предельного значения для локального тома (например, C:, D:).|
|**volume_managed_xstore_iops**|ssNoversion|-Вывода на второй предельного значения для учетной записи внешнего хранилища.|
|**volume_external_xstore_iops**|ssNoversion|-Вывода на второй предельного значения для учетной записи удаленного хранения использует резервные копии базы данных SQL Azure и данных телеметрии.|
|**volume_type_local_iops**|ssNoversion|-Вывода на второй предельного значения для всех локальных томов.|
|**volume_type_managed_xstore_iops**|ssNoversion|-Вывода на второй предельного значения для всех учетных записей хранилища, используемые экземпляром.|
|**volume_type_external_xstore_iops**|ssNoversion|-Вывода на второй предельного значения для всех учетных записей внешнего хранилища, используемые резервные копии базы данных SQL Azure и данные телеметрии для экземпляра.|
|**volume_pfs_iops**|ssNoversion|-Вывода на второй предельного значения для уровня "премиум" хранилище файлов.|
|**volume_type_pfs_iops**|ssNoversion|-Вывода на второй предельного значения для всех файлов хранилища класса premium, используемые экземпляром.|
|||

## <a name="permissions"></a>Разрешения

Для этого представления необходимо разрешение VIEW DATABASE STATE.

## <a name="remarks"></a>Примечания

Это динамическое административное представление для ресурсов управления конфигурации и параметры емкости для базы данных SQL Azure баз данных пользователям. 

> [!IMPORTANT]
> Большая часть данных, созданным это динамическое административное Представление предназначен для внутреннего использования и подлежит изменению.

## <a name="examples"></a>Примеры

В следующем примере возвращается экземпляр Максимальная скорость журналом упорядоченные по имени базы данных на сервере базы данных для базы данных одной или в составе пула.

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>См. также

- [Управление скорость журнала транзакций](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ограничения ресурсов DTU для отдельной базы данных](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Ограничения ресурсов виртуальное отдельной базы данных](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
