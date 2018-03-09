---
title: "sp_adddistributiondb (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_adddistributiondb_TSQL
- sp_adddistributiondb
helpviewer_keywords:
- sp_adddistributiondb
ms.assetid: e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6657074bade1db3cb050d6ca0c33e358d05e5f0c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spadddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новую базу данных распространителя и устанавливает схему Distributor. В базе данных распространителя хранятся процедуры, схема и метаданные, используемые при репликации. С помощью этой хранимой процедуры на стороне распространителя в базе данных master создается база данных распространителя и устанавливаются необходимые таблицы и хранимые процедуры, которые требуются для включения распространения репликации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adddistributiondb [ @database= ] 'database'   
    [ , [ @data_folder= ] 'data_folder' ]   
    [ , [ @data_file= ] 'data_file' ]   
    [ , [ @data_file_size= ] data_file_size ]   
    [ , [ @log_folder= ] 'log_folder' ]   
    [ , [ @log_file= ] 'log_file' ]   
    [ , [ @log_file_size= ] log_file_size ]   
    [ , [ @min_distretention= ] min_distretention ]   
    [ , [ @max_distretention= ] max_distretention ]   
    [ , [ @history_retention= ] history_retention ]   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @createmode= ] createmode ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@database=**] *базы данных "*  
 Имя создаваемой базы данных распространителя. *База данных* — **sysname**, не имеет значения по умолчанию. Если указанная база данных существует и не помечена как база данных распространителя, то устанавливаются объекты, необходимые для включения распространения, и база данных помечается как база данных распространителя. Если указанная база данных уже включена как база данных распространителя, то возвращается сообщение об ошибке.  
  
 [  **@data_folder=**] **"***data_folder"*  
 Имя каталога для хранения файла данных в базе данных распространителя. *data_folder* — **nvarchar(255)**, значение по умолчанию NULL. Если аргумент имеет значение NULL, то используется каталог данных для текущего экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, «`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`»).  
  
 [  **@data_file=**] **"***data_file***"**  
 Имя файла базы данных. *data_file* — **nvarchar(255)**, значение по умолчанию **базы данных**. Если аргумент имеет значение NULL, то хранимая процедура создает имя файла на основе имени базы данных.  
  
 [  **@data_file_size=**] *data_file_size*  
 Первоначальный размер файла данных в мегабайтах (МБ). *data_file_size я*s **int**, значение по умолчанию 5 МБ.  
  
 [  **@log_folder=**] **"***log_folder***"**  
 Имя каталога для файла журнала базы данных. *log_folder* — **nvarchar(255)**, значение по умолчанию NULL. Если аргумент имеет значение NULL, то используется каталог данных для текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например: «`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`».  
  
 [  **@log_file=**] **"***файл_журнала***"**  
 Имя файла журнала. *файл_журнала* — **nvarchar(255)**, значение по умолчанию NULL. Если аргумент имеет значение NULL, то хранимая процедура создает имя файла на основе имени базы данных.  
  
 [  **@log_file_size=**] *log_file_size*  
 Первоначальный размер файла журнала в мегабайтах (МБ). *log_file_size* — **int**, значение по умолчанию 0 МБ, то есть размер файла создается с помощью наименьшее журнала файла размера, разрешенного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [  **@min_distretention=**] *min_distretention*  
 Минимальный срок хранения до удаления транзакций из базы данных распространителя (в часах). *min_distretention* — **int**, значение по умолчанию 0 часов.  
  
 [  **@max_distretention=**] *max_distretention*  
 Максимальный срок хранения до удаления транзакций (в часах). *max_distretention* — **int**, значение по умолчанию 72 часа. Подписки, не получившие реплицируемые команды и хранящиеся дольше, чем позволяет значение максимального срока хранения, помечаются как неактивные; их необходимо повторно инициализировать. Для каждой неактивной подписки выполняется инструкция RAISERROR 21011. Значение **0** означает, что реплицируемые транзакции не хранятся в базе данных распространителя.  
  
 [  **@history_retention=**] *history_retention*  
 Время хранения журнала (в часах). *history_retention* — **int**, значение по умолчанию 48 часов.  
  
 [  **@security_mode=**] *security_mode*  
 Режим безопасности, используемый для подключения к распространителю. *security_mode* — **int**, значение по умолчанию 1. **0** указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности. **1** задает встроенную проверку подлинности Windows.  
  
 [  **@login=**] **"***входа***"**  
 Имя входа, которое используется при подключении к распространителю для создания базы данных распространителя. Требуется, если *security_mode* равно **0**. *Имя входа* — **sysname**, значение по умолчанию NULL.  
  
 [  **@password=**] **"***пароль***"**  
 Пароль, используемый при подключении к распространителю. Требуется, если *security_mode* равно **0**. *пароль* — **sysname**, значение по умолчанию NULL.  
  
 [  **@createmode=**] *createmode*  
 *createmode* — **int**, значение по умолчанию 1, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (по умолчанию)|Создание базы данных или использование существующей базы данных, а затем применить **instdist.sql** файла для создания объектов репликации в базе данных распространителя.|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 [  **@from_scripting =** ] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_adddistributiondb** используется во всех типах репликации. Однако эта хранимая процедура может выполняться только на стороне распространителя.  
  
 Необходимо настроить распространитель, выполнив [sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) перед выполнением **sp_adddistributiondb**.  
  
 Запустите **sp_adddistributor** перед выполнением **sp_adddistributiondb**.  
  
## <a name="example"></a>Пример  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_adddistributiondb**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
