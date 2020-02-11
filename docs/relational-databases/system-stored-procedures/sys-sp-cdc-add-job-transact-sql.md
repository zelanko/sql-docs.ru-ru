---
title: sys. sp_cdc_add_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7dd10d28855cc4c10f5496c74f1f39a91826052f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106537"
---
# <a name="syssp_cdc_add_job-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
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
`[ @job_type = ] 'job\_type'`Тип добавляемого задания. *job_type* имеет тип **nvarchar (20)** и не может иметь значение null. Допустимые входные данные: **"Capture"** и **"Cleanup"**.  
  
`[ @start_job = ] start_job`Флаг, указывающий, следует ли запускать задание сразу после его добавления. *start_job* имеет **бит** со значением по умолчанию 1.  
  
`[ @maxtrans ] = max_trans`Максимальное количество транзакций, обрабатываемых в каждом цикле просмотра. *max_trans* имеет **тип int** и значение по умолчанию 500. Указываемое значение должно быть положительным целым числом.  
  
 *max_trans* допустимы только для заданий отслеживания.  
  
`[ @maxscans ] = max\_scans_`Максимальное число циклов просмотра, которое необходимо выполнить для извлечения всех строк из журнала. *max_scans* имеет **тип int** и значение по умолчанию 10.  
  
 *max_scan* допустимы только для заданий отслеживания.  
  
`[ @continuous ] = continuous_`Указывает, должно ли задание отслеживания выполняться непрерывно (1) или выполняться только один раз (0). параметр *Continuous* имеет **бит** и значение по умолчанию 1.  
  
 Если *Continuous* = 1, задание [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) сканирует журнал и обрабатывает транзакции до (*max_trans* \* *max_scans*). Затем он ожидает число секунд, указанное в *polling_interval* , перед началом следующего просмотра журнала.  
  
 Если *Continuous* = 0, **sp_cdc_scan** задание выполняется до *max_scans* просмотров журнала, обработки до *max_trans* транзакции во время каждого сканирования, а затем завершает работу.  
  
 *Непрерывная* допустима только для заданий отслеживания.  
  
`[ @pollinginterval ] = polling\_interval_`Количество секунд между циклами просмотра журнала. *polling_interval* имеет тип **bigint** и значение по умолчанию 5.  
  
 *polling_interval* является допустимым только для заданий отслеживания, если параметр *Continuous* установлен в значение 1. Если значение указано, то оно не может быть отрицательным или превышать 24 часа. Если указано значение 0, то пауза между операциями просмотра журналов отсутствует.  
  
`[ @retention ] = retention_`Количество минут, в течение которых строки данных изменения должны храниться в таблицах изменений. параметр *retention* имеет тип **bigint** и значение по умолчанию 4320 (72 часов). Максимальное значение составляет 52494800 (100 лет). Указываемое значение должно быть положительным целым числом.  
  
 *Хранение* допустимо только для заданий очистки.  
  
`[ @threshold = ] 'delete\_threshold'`Максимальное число записей удаления, которые могут быть удалены с помощью одной инструкции при очистке. *delete_threshold* имеет тип **bigint** и значение по умолчанию 5000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Если для первой таблицы включена система отслеживания измененных данных, при создании задания очистки используются значения по умолчанию. Если для первой таблицы включена система отслеживания измененных данных и в базе данных не существует публикаций транзакций, при создании задания отслеживания используются значения по умолчанию. Если существует публикация транзакций, для работы механизма записи используется агент чтения журнала в репликации транзакций, а отдельное задание отслеживания не требуется и не допускается.  
  
 Так как задания очистки и отслеживания создаются по умолчанию, данная хранимая процедура используется только в тех случаях, когда задание необходимо повторно создать после выполнения явного удаления.  
  
 Имя задания — **CDC.** Очистка имени _\>базы данных\_ \<_ **CDC.** **\_** запись имени _\>базы данных, где<database_name>— имя текущей базы данных.\_ \<_**\_** ** Если задание с таким именем уже существует, к имени добавляется точка (**.**), за которой следует уникальный идентификатор, например: **CDC. AdventureWorks_capture. A1ACBDED-13FC-428C-8302-10100EF74F52**.  
  
 Чтобы просмотреть текущую конфигурацию задания очистки или записи, используйте [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md). Чтобы изменить конфигурацию задания, используйте [sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [Об SQL Server &#40;системы отслеживания измененных данных&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
