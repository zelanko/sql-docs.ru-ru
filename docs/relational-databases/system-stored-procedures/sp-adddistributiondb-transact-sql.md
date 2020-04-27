---
title: sp_adddistributiondb (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributiondb_TSQL
- sp_adddistributiondb
helpviewer_keywords:
- sp_adddistributiondb
ms.assetid: e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ef595adcf3772dcac92c58764d99bca4374aeb0a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68771352"
---
# <a name="sp_adddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
    [ , [ @deletebatchsize_xact = ] deletebatchsize_xact ] 
    [ , [ @deletebatchsize_cmd = ] deletebatchsize_cmd ] 
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] database'`Имя создаваемой базы данных распространителя. Аргумент *Database* имеет тип **sysname**и не имеет значения по умолчанию. Если указанная база данных существует и не помечена как база данных распространителя, то устанавливаются объекты, необходимые для включения распространения, и база данных помечается как база данных распространителя. Если указанная база данных уже включена как база данных распространителя, то возвращается сообщение об ошибке.  
  
`[ @data_folder = ] 'data_folder'_`Имя каталога, используемого для хранения файла данных базы данных распространителя. *DATA_FOLDER* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Если значение равно null, используется каталог данных для этого [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, например `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`.  
  
`[ @data_file = ] 'data_file'`Имя файла базы данных. *data_file* имеет тип **nvarchar (255)** и значение по умолчанию **Database**. Если аргумент имеет значение NULL, то хранимая процедура создает имя файла на основе имени базы данных.  
  
`[ @data_file_size = ] data_file_size`Начальный размер файла данных в мегабайтах (МБ). *data_file_size i* **int**и значение по умолчанию 5 МБ.  
  
`[ @log_folder = ] 'log_folder'`Имя каталога для файла журнала базы данных. *log_folder* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Если аргумент имеет значение NULL, то используется каталог данных для текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например: «`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`».  
  
`[ @log_file = ] 'log_file'`Имя файла журнала. *log_file* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Если аргумент имеет значение NULL, то хранимая процедура создает имя файла на основе имени базы данных.  
  
`[ @log_file_size = ] log_file_size`Начальный размер файла журнала в мегабайтах (МБ). *log_file_size* имеет **тип int**и значение по умолчанию 0 МБ, что означает, что размер файла создается с минимальным размером файла журнала, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешенным.  
  
`[ @min_distretention = ] min_distretention`Минимальный срок хранения (в часах) перед удалением транзакций из базы данных распространителя. *min_distretention* имеет **тип int**и значение по умолчанию 0 часов.  
  
`[ @max_distretention = ] max_distretention`Максимальный срок хранения (в часах) перед удалением транзакций. *max_distretention* имеет **тип int**и значение по умолчанию 72 часов. Подписки, не получившие реплицируемые команды и хранящиеся дольше, чем позволяет значение максимального срока хранения, помечаются как неактивные; их необходимо повторно инициализировать. Для каждой неактивной подписки выполняется инструкция RAISERROR 21011. Значение **0** означает, что реплицированные транзакции не хранятся в базе данных распространителя.  
  
`[ @history_retention = ] history_retention`Число часов, в течение которых будет храниться журнал. *history_retention* имеет **тип int**и значение по умолчанию 48 часов.  
  
`[ @security_mode = ] security_mode`Режим безопасности, используемый при соединении с распространителем. *security_mode* имеет **тип int**и значение по умолчанию 1. **0** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности; **1** указывает встроенную проверку подлинности Windows.  
  
`[ @login = ] 'login'`Имя входа, используемое при соединении с распространителем для создания базы данных распространителя. Это необходимо, если параметру *security_mode* присвоено значение **0**. Аргумент *login* имеет тип **sysname** и значение по умолчанию NULL.  
  
`[ @password = ] 'password'`Пароль, используемый при соединении с распространителем. Это необходимо, если параметру *security_mode* присвоено значение **0**. Аргумент *Password* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @createmode = ] createmode`*createmode* имеет **тип int**, значение по умолчанию 1 и может принимать одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (по умолчанию)|Создайте базу данных или используйте существующую базу данных, а затем примените файл **инстдист. SQL** , чтобы создать объекты репликации в базе данных распространителя.|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
 
`[ @deletebatchsize_xact = ] deletebatchsize_xact`Указывает размер пакета, который будет использоваться при очистке просроченных транзакций из MSRepl_Transactionsных таблиц. *deletebatchsize_xact* имеет **тип int**и значение по умолчанию 5000. Этот параметр впервые появился в SQL Server 2017, за которыми следуют выпуски SQL Server 2012 SP4 и SQL Server 2016 с пакетом обновления 2 (SP2).  

`[ @deletebatchsize_cmd = ] deletebatchsize_cmd`Указывает размер пакета, который будет использоваться во время очистки просроченных команд из таблиц MSRepl_Commands. *deletebatchsize_cmd* имеет **тип int**и значение по умолчанию 2000. Этот параметр впервые появился в SQL Server 2017, за которыми следуют выпуски SQL Server 2012 SP4 и SQL Server 2016 с пакетом обновления 2 (SP2). 
 
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **sp_adddistributiondb** используется во всех типах репликации. Однако эта хранимая процедура может выполняться только на стороне распространителя.  
  
 Необходимо настроить распространитель, выполнив [sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) перед выполнением **sp_adddistributiondb**.  
  
 Запустите **sp_adddistributor** перед запуском **sp_adddistributiondb**.  
  
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
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_adddistributiondb**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
