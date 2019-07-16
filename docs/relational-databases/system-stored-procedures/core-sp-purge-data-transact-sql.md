---
title: Core.sp_purge_data (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_purge_data_TSQL
- sp_purge_data
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_data
- management data warehouse, data collector stored procedures
- core.sp_purge_data stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 056076c3-8adf-4f51-8a1b-ca39696ac390
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72737a9b623e7979617784c1ef49c3f6d09aaea8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942495"
---
# <a name="coresppurgedata-transact-sql"></a>core.sp_purge_data (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет данные из хранилища данных управления в соответствии со стратегией хранения. Эта процедура выполняется ежедневно заданием mdw_purge_data агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применительно к хранилищу данных управления, связанному с определенным экземпляром. Эта хранимая процедура предназначена для удаления данных из хранилища данных управления по требованию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@retention_days =] *retention_days*  
 Число дней хранения данных в таблицах хранилища данных управления. Данные, имеющие отметку времени старше *retention_days* удаляется. *retention_days* — **smallint**, значение по умолчанию NULL. Указываемое значение должно быть положительным числом. Если задано значение NULL, то значение в столбце valid_through представления core.snapshots определяет строки, подлежащие удалению.  
  
 [@instance_name =] '*имя_экземпляра*"  
 Имя экземпляра набора элементов сбора. *имя_экземпляра* — **sysname**, значение по умолчанию NULL.  
  
 *имя_экземпляра* должно быть полным именем экземпляра, который состоит из имени компьютера и имя экземпляра в виде *computername*\\*instancename*. Если параметр имеет значение NULL, то используется экземпляр по умолчанию на локальном сервере.  
  
 [@collection_set_uid =] '*collection_set_uid*"  
 Имеет значение GUID для набора элементов сбора. *Аргумент collection_set_uid* — **uniqueidentifier**, значение по умолчанию NULL. Если он имеет значение NULL, то удаляются уточняющие строки из всех наборов элемента сбора. Чтобы получить это значение, выполните запрос к представлению каталога syscollector_collection_sets.  
  
 [@duration =] *длительность*  
 Максимальное число минут для выполнения операции очистки. *длительность* — **smallint**, значение по умолчанию NULL. Указываемое значение должно быть больше или равно нулю. Если оно имеет значение NULL, то операция выполняется до тех пор, пока все уточняющие строки не будут удалены либо операция не будет остановлена вручную.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Эта процедура выбирает строки в представлении core.snapshots, которые подлежат удалению в соответствии со сроком хранения. Все такие строки удаляются из таблицы core.snapshots_internal. Удаление устаревших строк приводит к каскадному удалению строк во всех таблицах хранилища данных управления. Указанная процедура выполняется с помощью предложения ON DELETE CASCADE, которое определено для всех таблиц, в которых хранятся собранные данные.  
  
 Каждый моментальный снимок и связанные с ним данные удаляются в пределах явной транзакции, а затем транзакция фиксируется. Таким образом Если операция по очистке остановлена вручную, или значение, заданное для @duration превышен, только незафиксированные данные остаются. Эти данные могут быть удалены во время следующего запуска задания.  
  
 Эта процедура должна выполняться в контексте базы данных хранилища данных управления.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **mdw_admin** (с разрешением EXECUTE) предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-running-sppurgedata-with-no-parameters"></a>A. Запуск процедуры sp_purge_data без параметров  
 В следующем примере выполняется процедура core.sp_purge_data без параметров. Поэтому для всех параметров используется значение по умолчанию (NULL) и выполняются действия, соответствующие этому значению.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>Б. Задание значений срока хранения и продолжительности операции  
 В следующем примере удаляются данные из хранилища данных управления, созданные более 7 дней назад. Кроме того @duration указан параметр, чтобы эта операция будет выполняться не более 5 минут.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>В. Задание имени экземпляра и набора элементов сбора  
 В следующем примере удаляются данные из хранилища данных управления для заданного набора сбора в указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Так как @retention_days не указан, значение в столбце valid_through представления core.snapshots используется для определения строк для набора сбора, подлежащие удалению.  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
