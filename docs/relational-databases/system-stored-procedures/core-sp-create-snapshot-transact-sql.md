---
title: Core.sp_create_snapshot (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33ba9d69763a9d07cc9907aef60397b6c5b37eee
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "33238571"
---
# <a name="corespcreatesnapshot-transact-sql"></a>core.sp_create_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вставляет строку в представление core.snapshots хранилища данных управления. Эта процедура вызывается каждый раз, когда пакет передачи начинает передавать данные в хранилище данных управления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @collection_set_uid =] '*аргумент collection_set_uid*"  
 Имеет значение GUID для набора элементов сбора. *Аргумент collection_set_uid* — **uniqueidentifier** без значения по умолчанию. Чтобы получить идентификатор GUID, запросите представление dbo.syscollector_collection_sets в базе данных msdb.  
  
 [ @collector_type_uid =] '*аргумент collector_type_uid*"  
 Идентификатор GUID для типа сборщика. *Аргумент collector_type_uid* — **uniqueidentifier** без значения по умолчанию. Чтобы получить идентификатор GUID, запросите представление dbo.syscollector_collector_types в базе данных msdb.  
  
 [ @machine_name=] '*имя_компьютера*"  
 Имя сервера, на котором находится набор элементов сбора. *имя_компьютера* — **sysname**, и не имеет значения по умолчанию.  
  
 [ @named_instance=] '*именованный_экземпляр*"  
 Имя экземпляра набора элементов сбора. *именованный_экземпляр* — **sysname**, и не имеет значения по умолчанию.  
  
 [ @log_id =] *log_id*  
 Уникальный идентификатор, соответствующий журналу событий набора элементов сбора на сервере, который собирал данные. *log_id* — **bigint** без значения по умолчанию. Для получения значения для *log_id*, запросите представление dbo.syscollector_execution_log в базе данных msdb.  
  
 [ @snapshot_id =] *snapshot_id*  
 Уникальный идентификатор для строки, вставляемой в представление core.snapshots. *snapshot_id* — **int** и возвращается как OUTPUT.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда пакет передачи начинает загружать данные в хранилище управляющих данных, исполняемый компонент сборщика данных вызывает функцию core.sp_create_snapshot.  
  
 Эта процедура проверяет следующее:  
  
-   Аргумент collection_set_uid соответствует существующей записи в таблице core.source_info_internal.  
  
-   Аргумент collector_type_uid соответствует существующей записи в представлении core.supported_collector_types.  
  
 Если хотя бы одно из вышеперечисленных условий не выполняется, процедура возвращает ошибку.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **mdw_writer** (с разрешением EXECUTE) предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается моментальный снимок для набора сбора «Занято места на диске», который добавляется в хранилище данных управления, а затем возвращается идентификатор моментального снимка. В примере используется экземпляр по умолчанию.  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Хранилище данных управления](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
