---
title: sys. sp_cdc_change_job (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 4bd906f9a359a73a15d89a4cb60b6646a2abe53a
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305061"
---
# <a name="syssp_cdc_change_job-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет конфигурацию задания очистки системы отслеживания измененных данных или задания записи в текущей базе данных. Чтобы просмотреть текущую конфигурацию задания, выполните запрос к таблице [dbo. CDC _jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) или используйте [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
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
@no__t — 0 тип задания для изменения. *job_type* имеет тип **nvarchar (20)** и значение по умолчанию "Capture". Допустимы следующие варианты ввода: «capture» и «cleanup».  
  
`[ @maxtrans ] = max_trans_` максимальное количество транзакций для обработки в каждом цикле просмотра. *max_trans* имеет **тип int** и значение по умолчанию NULL, которое указывает на отсутствие изменений для этого параметра. Указываемое значение должно быть положительным целым числом.  
  
 *max_trans* является допустимым только для заданий отслеживания.  
  
`[ @maxscans ] = max_scans_` максимальное число циклов просмотра для выполнения, чтобы извлечь все строки из журнала. *max_scans* имеет **тип int** и значение по умолчанию NULL, которое указывает на отсутствие изменений для этого параметра.  
  
 *max_scan* является допустимым только для заданий отслеживания.  
  
`[ @continuous ] = continuous_` указывает, должно ли задание отслеживания выполняться непрерывно (1) или выполняться только один раз (0). параметр *Continuous* имеет **бит** и значение по умолчанию NULL, что означает отсутствие изменений для этого параметра.  
  
 Если *Continuous* = 1, задание [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) сканирует журнал и обрабатывает транзакции до (*max_trans* \* *max_scans*). Затем он ожидает число секунд, указанное в *polling_interval* , перед началом следующего просмотра журнала.  
  
 Если *Continuous* = 0, задание **sp_cdc_scan** выполняется до *max_scans* просмотров журнала, обработки до *max_trans* транзакций во время каждого сканирования, а затем завершает работу.  
  
 Если параметр **\@continuous** изменен с 1 на 0, **\@pollinginterval** автоматически устанавливается в значение 0. Значение, указанное для **\@pollinginterval** , отличное от 0, игнорируется.  
  
 Если параметр **\@continuous** опущен или явно задано значение null, а **\@pollinginterval** явно задано значение больше 0, **\@continuous** автоматически устанавливается в 1.  
  
 *Непрерывная* допустима только для заданий отслеживания.  
  
`[ @pollinginterval ] = polling_interval_` число секунд между циклами просмотра журнала. *polling_interval* имеет тип **bigint** и значение по умолчанию NULL, которое указывает на отсутствие изменений для этого параметра.  
  
 *polling_interval* является допустимым только для заданий отслеживания, если параметр *Continuous* установлен в значение 1.  
  
`[ @retention ] = retention_` — количество минут, в течение которых строки изменений должны храниться в таблицах изменений. параметр *retention* имеет тип **bigint** и значение по умолчанию NULL, которое указывает на отсутствие изменений для этого параметра. Максимальное значение составляет 52494800 (100 лет). Указываемое значение должно быть положительным целым числом.  
  
 *Хранение* допустимо только для заданий очистки.  
  
`[ @threshold = ] 'delete threshold'` максимальное число записей удаления, которые можно удалить с помощью одной инструкции при очистке. *пороговое значение удаления* — **bigint** и значение по умолчанию NULL, которое указывает на отсутствие изменений для этого параметра. *порог удаления* допустим только для заданий очистки.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Если параметр не указан, связанное значение в таблице [dbo. CDC _jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) не обновляется. Явное присвоение параметру значения NULL эквивалентно его пропусканию.  
  
 Указание недопустимого для типа задания параметра приведет к ошибке при выполнении инструкции.  
  
 Изменения в задании вступают в силу только после остановки задания с помощью [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) и перезапуска с помощью [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-a-capture-job"></a>A. Изменение задания отслеживания  
 В следующем примере выполняется обновление параметров `@job_type`, `@maxscans` и `@maxtrans` задания отслеживания в базе данных `AdventureWorks2012`. Другие допустимые параметры задания отслеживания (`@continuous` и `@pollinginterval`) пропущены; их значения не изменяются.  
  
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
 В следующем примере обновляется задание очистки базы данных `AdventureWorks2012`. Указаны все допустимые параметры для этого типа задания, кроме **@threshold** . Значение **@threshold** не изменяется.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [dbo. CDC _jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
