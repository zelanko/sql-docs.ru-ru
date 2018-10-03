---
title: sys.sp_cdc_change_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f2aa4413bd9f226bd0bbdf5b676da0da866fde32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705862"
---
# <a name="sysspcdcchangejob-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет конфигурацию задания очистки системы отслеживания измененных данных или задания записи в текущей базе данных. Чтобы просмотреть текущую конфигурацию задания, запросите [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) таблицы либо использовать [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
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
 Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра. *max_trans* — **int** и по умолчанию NULL, которое указывает, этот параметр не изменяется. Указываемое значение должно быть положительным целым числом.  
  
 *max_trans* допустим только для заданий записи.  
  
 [ **@maxscans** ] **= *** max_scans*  
 Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала. *max_scans* — **int** и по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 *max_scan* допустим только для заданий записи.  
  
 [ **@continuous** ] **= *** непрерывной*  
 Указывает, должно ли задание отслеживания выполняться постоянно (1) или только один раз (0). *Непрерывная* — **бит** и по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 Когда *непрерывной* = 1, [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) задания просматривает журнал и обрабатывает до (*max_trans* \* *max_scans*) транзакции. Затем ожидается число секунд, указанных в *polling_interval* перед началом следующего просмотра журнала.  
  
 Когда *непрерывной* = 0, **sp_cdc_scan** задание выполняет до *max_scans* просмотров журнала, обрабатывая до *max_trans* транзакций во время каждого сканирования и затем завершает работу.  
  
 Если **@continuous** меняется с 1 на 0, **@pollinginterval** автоматически устанавливается значение 0. Значение, указанное для **@pollinginterval** отличные от 0 учитывается.  
  
 Если **@continuous** опущен или явно установлен в значение NULL и **@pollinginterval** явно присвоено значение больше 0, **@continuous** автоматически значение 1.  
  
 *Непрерывная* допустим только для заданий записи.  
  
 [ **@pollinginterval** ] **= *** polling_interval*  
 Число секунд между циклами просмотра журнала. *polling_interval* — **bigint** и по умолчанию NULL, которое указывает, этот параметр не изменяется.  
  
 *polling_interval* допустим только для отслеживания заданий при *непрерывной* имеет значение 1.  
  
 [ **@retention** ] **= *** хранения*  
 Число минут, в течение которого строки изменений должны храниться в таблицах изменений. *хранение* — **bigint** и по умолчанию NULL, которое указывает, этот параметр не изменяется. Максимальное значение составляет 52494800 (100 лет). Указываемое значение должно быть положительным целым числом.  
  
 *хранение* допустим только для заданий очистки.  
  
 [  **@threshold=** ] **"***удалить пороговое значение***"**  
 Максимальное число записей, подлежащих удалению, которые могут быть удалены одной инструкцией при очистке. *удалить пороговое значение* — **bigint** и по умолчанию NULL, которое указывает, этот параметр не изменяется. *удалить пороговое значение* допустим только для заданий очистки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Если параметр пропущен, связанного значения в [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) обновляется. Явное присвоение параметру значения NULL эквивалентно его пропусканию.  
  
 Указание недопустимого для типа задания параметра приведет к ошибке при выполнении инструкции.  
  
 Изменения в задании не вступают в силу до остановки задания с помощью [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) и перезапустить с помощью [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md).  
  
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
 [sys.sp_cdc_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
