---
title: sys. DM _user_db_resource_governance (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: ea07ba28efc4ac50fdeef04bb1b3643c359ead28
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176255"
---
# <a name="sysdm_user_db_resource_governance-transact-sql"></a>sys. DM _user_db_resource_governance (Transact-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Возвращает параметры конфигурации и емкости управления ресурсами для базы данных SQL Azure.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|int|Идентификатор базы данных, уникальный на сервере базы данных SQL Azure.|
|**logical_database_guid**|UNIQUEIDENTIFIER|Логический идентификатор GUID для пользовательской базы данных и остается в течение жизненного цикла пользовательской базы данных.  Переименование или Настройка базы данных на другую цель уровня обслуживания не приведет к изменению идентификатора GUID. |
|**physical_database_guid**|UNIQUEIDENTIFIER|Физический идентификатор GUID для пользовательской базы данных, который остается в течение всего времени существования физического экземпляра пользовательской базы данных. Если задать другую цель уровня обслуживания, этот столбец будет изменен.|
|**server_name**|nvarchar|Имя логического сервера.|
|**database_name**|nvarchar|Имя логической базы данных.|
|**slo_name**|nvarchar|Цель уровня обслуживания и создание оборудования.|
|**dtu_limit**|int|Предел DTU базы данных (NULL для Виртуальное ядро).|
|**cpu_limit**|int|Виртуальное ядро ограничение базы данных (значение NULL для баз данных DTU).|
|**min_cpu**|tinyint|Минимальный процент загрузки ЦП, который может использоваться рабочей нагрузкой пользователя.|
|**max_cpu**|tinyint|Максимальный процент загрузки ЦП, который может использоваться рабочей нагрузкой пользователя.|
|**cap_cpu**|tinyint|Ограничение процента загрузки ЦП для групп рабочей нагрузки пользователя.|
|**min_cores**|smallint|Количество ЦП, используемых SQL.|
|**max_dop**|smallint|Максимальная степень параллелизма, используемая пользовательской рабочей нагрузкой.|
|**min_memory**|int|Минимальный процент использования памяти, который может использоваться рабочей нагрузкой пользователя.|
|**max_memory**|int|Максимальный процент использования памяти, который может использоваться рабочей нагрузкой пользователя.|
|**max_sessions**|int|Ограничение числа сеансов для группы пользователей.|
|**max_memory_grant**|int|Максимальный объем выделения памяти для каждого запроса в рабочей нагрузке пользователя в процентах.|
|**max_db_memory**|int|Максимальный предел памяти буферного пула для рабочей нагрузки пользовательской базы данных|
|**govern_background_io**|bit|Указывает, начисляются ли записи в фоновом режиме для группы пользователей.|
|**min_db_max_size_in_mb**|bigint|Минимальный максимальный размер файла базы данных в МБ.|
|**max_db_max_size_in_mb**|bigint|Максимальный размер файла базы данных в МБ.|
|**default_db_max_size_in_mb**|bigint|Максимальный размер файла базы данных по умолчанию (в МБ).|
|**db_file_growth_in_mb**|bigint|Рост размера файла базы данных Azure по умолчанию в МБ.|
|**initial_db_file_size_in_mb**|bigint|Размер файла базы данных по умолчанию (в МБ).|
|**log_size_in_mb**|bigint|Размер файла журнала по умолчанию (в МБ).|
|**instance_cap_cpu**|int|Ограничение ЦП на уровне экземпляра.|
|**instance_max_log_rate**|bigint|Ограничение скорости формирования журнала на уровне экземпляра (в байтах в секунду).|
|**instance_max_worker_threads**|int|Ограничение рабочего потока на уровне экземпляра.|
|**replica_type**|int|Тип реплики, где 0 — первичный, а 1 — вторичный.|
|**max_transaction_size**|bigint|Максимальное пространство журнала, используемое любой транзакцией, в КБ.|
|**checkpoint_rate_mbps**|int|Пропускная способность контрольной точки в Мбит/с.|
|**checkpoint_rate_io**|int|Скорость ввода-вывода контрольной точки в IOs в секунду.|
|**last_updated_date_utc**|datetime|Дата и время последнего изменения параметра или его настройки.|
|**primary_group_id**|int|Идентификатор группы рабочей нагрузки основного пользователя.|
|**primary_group_max_workers**|int|Ограничение рабочей роли на уровне группы рабочей нагрузки основного пользователя.|
|**primary_min_log_rate**|bigint|Минимальная частота журнала (байт/с) на уровне группы рабочей нагрузки основного пользователя.|
|**primary_max_log_rate**|bigint|Максимальная скорость журнала (байт/с) на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_min_io**|int|Минимальный уровень ввода-вывода на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_max_io**|int|Максимальное количество операций ввода-вывода на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_min_cpu**|float|Минимальный процент использования ЦП на уровне группы рабочей нагрузки основного пользователя.|
|**primary_group_max_cpu**|float|Максимальный процент использования ЦП на уровне группы рабочей нагрузки основного пользователя.|
|**primary_log_commit_fee**|int|Тариф на фиксацию управления скоростью ведения журнала на уровне группы рабочей нагрузки основного пользователя.|
|**primary_pool_max_workers**|int|Ограничение рабочей роли на уровне основного пула пользователей.
|**pool_max_io**|int|Максимальный предел ввода-вывода на уровне основного пула пользователей.|
|**govern_db_memory_in_resource_pool**|bit|Указывает, регулируется ли максимальный размер буферного пула на уровне пула ресурсов. Обычно задается для баз данных в эластичных пулах.|
|**volume_local_iops**|int|Ограничение IOs в секунду для локального тома (например, C:, D:).|
|**volume_managed_xstore_iops**|int|Ограничение IOs в секунду для учетной записи удаленного хранилища.|
|**volume_external_xstore_iops**|int|Ограничение IOs в секунду для учетной записи удаленного хранилища, используемой резервными копиями и телеметрии базы данных SQL Azure.|
|**volume_type_local_iops**|int|Ограничение IOs в секунду для всех локальных томов.|
|**volume_type_managed_xstore_iops**|int|Ограничение IOs в секунду для всех удаленных учетных записей хранения, используемых экземпляром.|
|**volume_type_external_xstore_iops**|int|Ограничение IOs в секунду для всех удаленных учетных записей хранения, используемых резервными копиями и данными телеметрии базы данных SQL Azure для экземпляра.|
|**volume_pfs_iops**|int|Ограничение IOs в секунду для хранилища файлов класса Premium.|
|**volume_type_pfs_iops**|int|Ограничение IOs в секунду для всех хранилищ файлов класса Premium, используемых экземпляром.|
|||

## <a name="permissions"></a>Разрешения

Для этого представления необходимо разрешение VIEW DATABASE STATE.

## <a name="remarks"></a>Примечания

Пользователи могут получить доступ к этому динамическому административному представлению для конфигурации управления ресурсами и настройки емкости для базы данных SQL Azure. 

> [!IMPORTANT]
> Большая часть данных, предоставляемых этим динамическим административным представлением, предназначена для внутреннего использования и может изменяться.

## <a name="examples"></a>Примеры

В следующем примере возвращаются максимальные данные о скорости журнала экземпляра, упорядоченные по имени базы данных на сервере базы данных для отдельной базы данных или в составе пула.

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>См. также

- [Управление частотой ведения журнала транзакций](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Ограничения ресурсов DTU одной базы данных](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [Ограничения ресурсов для одной базы данных Виртуальное ядро](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
