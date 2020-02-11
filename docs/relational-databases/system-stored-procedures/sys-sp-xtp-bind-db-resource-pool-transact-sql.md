---
title: sys. sp_xtp_bind_db_resource_pool (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xtp_bind_db_resource_pool_TSQL
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool_TSQL
- sys.sp_xtp_bind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool
ms.assetid: c2a78073-626b-4159-996e-1808f6bfb6d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: af0e10f23d376c96fd7be0a75cf713dd76a2c149
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041008"
---
# <a name="syssp_xtp_bind_db_resource_pool-transact-sql"></a>sys.sp_xtp_bind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Привязывает указанную базу данных служб [!INCLUDE[hek_2](../../includes/hek-2-md.md)] к указанному пулу ресурсов. И база данных, и пул ресурсов должны существовать до выполнения `sys.sp_xtp_bind_db_resource_pool`.  
  
 Эта системная процедура создает привязку между пулом Resource Governor, определяемого resource_pool_name, и базой данных, определяемой database_name. Наличие во время привязки в базе данных каких-либо объектов, которые оптимизированы для памяти, не является обязательным. При отсутствии объектов, оптимизированных для памяти, из пула ресурсов не изымаются ресурсы памяти. Эта привязка будет использоваться Resource Governor для управления памятью, выделенной распределителями [!INCLUDE[hek_2](../../includes/hek-2-md.md)], как описано ниже.  
  
 Если уже существует привязка для конкретной базы данных, процедура возвращает ошибку.  Ни при каких обстоятельствах база данных не может иметь более одной активной привязки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sys.sp_xtp_bind_db_resource_pool 'database_name', 'resource_pool_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 database_name  
 Имя существующей базы данных с подключенными [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  
  
 resource_pool_name  
 Имя существующего пула ресурсов.  
  
## <a name="messages"></a>Сообщения  
 При возникновении ошибки `sp_xtp_bind_db_resource_pool` возвращает одно из этих сообщений.  
  
 **База данных не существует**  
 Database_name должен ссылаться на существующую базу данных. Если база данных с указанным идентификатором не существует, возвращается следующее сообщение:   
*Идентификатор базы данных% d не существует.  Используйте допустимый идентификатор базы данных для этой привязки.*  
  
```  
Msg 911, Level 16, State 18, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB213' does not exist. Make sure that the name is entered correctly.  
```  
  
**База данных является системной.**  
 Таблицы[!INCLUDE[hek_2](../../includes/hek-2-md.md)] нельзя создать в системных базах данных.  Таким образом, не допускается создание привязки памяти [!INCLUDE[hek_2](../../includes/hek-2-md.md)] для такой базы данных.  Возвращается следующая ошибка:  
*Database_name% s ссылается на системную базу данных.  Пулы ресурсов могут быть привязаны только к пользовательской базе данных.*  
  
```  
Msg 41371, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Binding to a resource pool is not supported for system database 'master'. This operation can only be performed on a user database.  
```  
  
**Пул ресурсов не существует**  
 Пул ресурсов, определяемый resource_pool_name, должен существовать до выполнения `sp_xtp_bind_db_resource_pool`.  Если пул с указанным идентификатором не существует, возвращается следующая ошибка:  
*Пул ресурсов% s не существует.  Укажите допустимое имя пула ресурсов.*  
  
```  
Msg 41370, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Resource pool 'Pool_Hekaton' does not exist or resource governor has not been reconfigured.  
```  
  
**Pool_name ссылается на зарезервированный системный пул**  
 Имена пулов "INTERNAL" и "DEFAULT" зарезервированы для системных пулов.  Явная привязка базы данных к одному из этих пулов недопустима.  Если введено имя системного пула, то возвращается следующая ошибка:  
*Пул ресурсов% s является пулом системных ресурсов.  Пулы системных ресурсов не могут быть явно привязаны к базе данных с помощью этой процедуры.*  
  
```  
Msg 41373, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB' cannot be explicitly bound to the resource pool 'internal'. A database can only be bound only to a user resource pool.  
```  
  
**База данных уже привязаны к другому пулу ресурсов**  
 База данных может быть привязана только к одному пулу ресурсов в любой момент времени. Привязки баз данных к пулам ресурсов необходимо явно удалить перед тем, как они могут быть привязаны к другому пулу. См. раздел [sys. sp_xtp_unbind_db_resource_pool &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md).  
*База данных% s уже привязана к пулу ресурсов% s.  Для создания новой привязки необходимо отменить привязку.*  
  
```  
Msg 41372, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 54  
Database 'Hekaton_DB' is currently bound to a resource pool. A database must be unbound before creating a new binding.  
```  
  
 При успешном выполнении `sp_xtp_bind_db_resource_pool` возвращает следующее сообщение.  
  
**Привязка успешно выполнена**  
 При успешном выполнении функция возвращает следующее сообщение об успешном выполнении, которое регистрируется в SQL ERRORLOG  
*Привязка ресурсов была успешно создана между базой данных с идентификатором %d и пулом ресурсов с идентификатором %d.*  
  
## <a name="examples"></a>Примеры  
A.  В следующем примере кода выполняется привязка базы данных Hekaton_DB с пулом ресурсов Pool_Hekaton.  
  
```sql  
sys.sp_xtp_bind_db_resource_pool N'Hekaton_DB', N'Pool_Hekaton'  
```  
 
 Привязка вступит в силу при следующем переводе базы данных в режим «в сети».  
 
 Б. Расширенный пример приведенного выше примера, который включает некоторые основные проверки.  Выполните следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию в[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]\:
 
```sql
DECLARE @resourcePool sysname = N'Pool_Hekaton';
DECLARE @database sysname = N'Hekaton_DB';

-- Check whether resource pool exists
IF NOT EXISTS (
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = @resourcePool
    )
BEGIN
    SELECT N'Resource pool "' + @resourcePool + N'" does not exist or resource governor has not been reconfigured.';
END
-- Check whether database is already bound to a resource pool
ELSE IF EXISTS (
    SELECT p.name
    FROM sys.databases d
    JOIN sys.resource_governor_resource_pools p
    ON d.resource_pool_id = p.pool_id
    WHERE d.name = @database
    )
BEGIN
    SELECT N'Database "' + @database + N'" is currently bound to resource pool "' + @resourcePool  + N'". A database must be unbound before creating a new binding.';
END
-- Bind resource pool to database.
ELSE BEGIN
    EXEC sp_xtp_bind_db_resource_pool @database, @resourcePool; 
END 
``` 
  
## <a name="requirements"></a>Требования  
  
-   И база данных, указанная с помощью `database_name`, и пул ресурсов, указанный с помощью `resource_pool_name`, должны существовать до их привязки.  
  
-   Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также:  
 [Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys. sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  
