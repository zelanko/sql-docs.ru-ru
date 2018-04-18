---
title: sys.sp_cdc_add_job (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cdc_add_job_TSQL
- sys.sp_cdc_add_job
- sys.sp_cdc_add_job_TSQL
- sp_cdc_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_add_job
ms.assetid: c4458738-ed25-40a6-8294-a26ca5a05bd9
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 58f17196962c2ca05ebf1c2e56ce78621dbb9ac7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysspcdcaddjob-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает задание очистки или записи системы отслеживания информации об изменениях в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_add_job [ @job_type = ] 'job_type'  
    [ , [ @start_job = ] start_job ]   
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ , [ @threshold ] = 'delete_threshold' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_type=** ] **"***job_type***"**  
 Тип добавляемого задания. *job_type* — **nvarchar(20)** и не может иметь значение NULL. Допустимыми входными значениями являются **'capture'** и **«cleanup»**.  
  
 [  **@start_job=** ] *start_job*  
 Флаг, показывающий, следует ли запускать задание сразу после его добавления. *start_job* — **бит** значение по умолчанию 1.  
  
 [ **@maxtrans** ] = *max_trans*  
 Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра. *max_trans* — **int** значение по умолчанию 500. Указываемое значение должно быть положительным целым числом.  
  
 *max_trans* допустим только для заданий записи.  
  
 [ **@maxscans** ] **= *** max_scans*  
 Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала. *max_scans* — **int** значение по умолчанию 10.  
  
 *max_scan* допустим только для заданий записи.  
  
 [ **@continuous** ] **= *** непрерывной*  
 Указывает, должно ли задание отслеживания выполняться постоянно (1) или только один раз (0). *непрерывные* — **бит** значение по умолчанию 1.  
  
 Когда *непрерывного* = 1, [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) задания просматривает журнал и обрабатывает до (*max_trans* \* *max_scans*) транзакции. Задание ожидает в течение указанного количества секунд в *интервал_опроса* перед началом следующего просмотра журнала.  
  
 Когда *непрерывного* = 0, **sp_cdc_scan** задание выполняет до *max_scans* просмотров журнала, обрабатывая до *max_trans* транзакций во время каждой проверки, а затем завершает работу.  
  
 *непрерывные* допустим только для заданий записи.  
  
 [ **@pollinginterval** ] **= *** интервал_опроса*  
 Число секунд между циклами просмотра журнала. *интервал_опроса* — **bigint** значение по умолчанию 5.  
  
 *интервал_опроса* допустимо только для захвата заданий при *непрерывного* имеет значение 1. Если значение указано, то оно не может быть отрицательным или превышать 24 часа. Если указано значение 0, то пауза между операциями просмотра журналов отсутствует.  
  
 [ **@retention** ] **= *** хранения*  
 Число минут, в течение которого строки данных об изменениях необходимо хранить в таблицах изменений. *хранения* — **bigint** значение по умолчанию 4320 (72 часа). Максимальное значение составляет 52494800 (100 лет). Указываемое значение должно быть положительным целым числом.  
  
 *хранения* допустим только для заданий очистки.  
  
 [  **@threshold =** ] **"***delete_threshold***"**  
 Максимальное число записей, подлежащих удалению, которые можно удалить с использованием одной инструкции при очистке. *delete_threshold* — **bigint** значение по умолчанию 5000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Если для первой таблицы включена система отслеживания измененных данных, при создании задания очистки используются значения по умолчанию. Если для первой таблицы включена система отслеживания измененных данных и в базе данных не существует публикаций транзакций, при создании задания отслеживания используются значения по умолчанию. Если существует публикация транзакций, для работы механизма записи используется агент чтения журнала в репликации транзакций, а отдельное задание отслеживания не требуется и не допускается.  
  
 Так как задания очистки и отслеживания создаются по умолчанию, данная хранимая процедура используется только в тех случаях, когда задание необходимо повторно создать после выполнения явного удаления.  
  
 Имя задания **cdc. ***< имя_базы_данных >***_cleanup** или **cdc. ***< имя_базы_данных >***_capture**, где *< имя_базы_данных >* имя текущей базы данных. Если задание с таким именем уже существует, к имени добавляется с периодом (**.**) и уникальным идентификатором, например: **cdc. AdventureWorks_capture. A1ACBDED-13FC-428C-8302-10100EF74F52**.  
  
 Для просмотра текущей конфигурации задания очистки или отслеживания, используйте [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md). Чтобы изменить конфигурацию задания, используйте [sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-capture-job"></a>A. Создание задания отслеживания  
 В следующем примере создается задание отслеживания. В этом примере предполагается, что существующее задание очистки было явным образом удалено и его необходимо создать повторно. Задание создается с использованием значений по умолчанию.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job @job_type = N'capture';  
GO  
```  
  
### <a name="b-creating-a-cleanup-job"></a>Б. Создание задания очистки  
 В следующем примере создается задание очистки в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Параметр `@start_job` имеет значение 0, а аргумент `@retention` — 5 760 минут (96 часов). В этом примере предполагается, что существующее задание очистки было явным образом удалено и его необходимо создать повторно.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job  
     @job_type = N'cleanup'  
    ,@start_job = 0  
    ,@retention = 5760;  
```  
  
## <a name="see-also"></a>См. также  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [Об отслеживании измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
