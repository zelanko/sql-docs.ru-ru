---
title: sys.sp_cdc_change_job (Transact-SQL) | Документы Microsoft
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
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48ea42d122c0b7431279ec53b384d400ea5f9de8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysspcdcchangejob-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет конфигурацию задания очистки системы отслеживания измененных данных или задания записи в текущей базе данных. Чтобы просмотреть текущую конфигурацию задания, запросите [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) таблице или используйте [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_type=** ] **"***job_type***"**  
 Тип задания для изменения. *job_type* — **nvarchar(20)** значение по умолчанию «Capture». Допустимы следующие варианты ввода: «capture» и «cleanup».  
  
 [ **@maxtrans** ] **= *** max_trans*  
 Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра. *max_trans* — **int** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется. Указываемое значение должно быть положительным целым числом.  
  
 *max_trans* допустим только для заданий записи.  
  
 [ **@maxscans** ] **= *** max_scans*  
 Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала. *max_scans* — **int** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 *max_scan* допустим только для заданий записи.  
  
 [ **@continuous** ] **= *** непрерывной*  
 Указывает, должно ли задание отслеживания выполняться постоянно (1) или только один раз (0). *непрерывные* — **бит** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 Когда *непрерывного* = 1, [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) задания просматривает журнал и обрабатывает до (*max_trans* \* *max_scans*) транзакции. Задание ожидает в течение указанного количества секунд в *интервал_опроса* перед началом следующего просмотра журнала.  
  
 Когда *непрерывного* = 0, **sp_cdc_scan** задание выполняет до *max_scans* просмотров журнала, обрабатывая до *max_trans* транзакций во время каждой проверки, а затем завершает работу.  
  
 Если **@continuous** меняется с 1 на 0, **@pollinginterval** автоматически устанавливается равным 0. Значение, указанное для **@pollinginterval** отличное от 0, учитывается.  
  
 Если **@continuous** опущен или явно установлен в значение NULL и **@pollinginterval** явно задано значение больше 0, **@continuous** автоматически Задайте значение 1.  
  
 *непрерывные* допустим только для заданий записи.  
  
 [ **@pollinginterval** ] **= *** интервал_опроса*  
 Число секунд между циклами просмотра журнала. *интервал_опроса* — **bigint** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 *интервал_опроса* допустимо только для захвата заданий при *непрерывного* имеет значение 1.  
  
 [ **@retention** ] **= *** хранения*  
 Число минут, в течение которого строки изменений должны храниться в таблицах изменений. *хранения* — **bigint** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется. Максимальное значение составляет 52494800 (100 лет). Указываемое значение должно быть положительным целым числом.  
  
 *хранения* допустим только для заданий очистки.  
  
 [  **@threshold=** ] **"***удалить пороговое значение***"**  
 Максимальное число записей, подлежащих удалению, которые могут быть удалены одной инструкцией при очистке. *удалить пороговое значение* — **bigint** и значение по умолчанию NULL, которое указывает, этот параметр не изменяется. *удалить порог* допустим только для заданий очистки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Если параметр опущен, соответствующее значение в [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) таблица не обновлена. Явное присвоение параметру значения NULL эквивалентно его пропусканию.  
  
 Указание недопустимого для типа задания параметра приведет к ошибке при выполнении инструкции.  
  
 Изменения в задании вступают в силу до остановки задания с помощью [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) и перезапустить с помощью [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-a-capture-job"></a>A. Изменение задания отслеживания  
 В следующем примере обновляется `@job_type`, `@maxscans`, и `@maxtrans` параметры задания отслеживания в `AdventureWorks2012` базы данных. Другие допустимые параметры задания отслеживания (`@continuous` и `@pollinginterval`) пропущены; их значения не изменяются.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>Б. Изменение задания очистки  
 В следующем примере обновляется задание очистки базы данных `AdventureWorks2012`. Все допустимые параметры для этого типа задания за исключением **@threshold**, указаны. Значение **@threshold** не изменяется.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
