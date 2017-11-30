---
title: "sys.sp_cdc_scan (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8cd29ff4ce371f6d893ceb396bb3a69d20bcab2
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет операцию просмотра журнала системы отслеживания измененных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@maxtrans=** ] *max_trans*  
 Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра. *max_trans* — **int** значение по умолчанию 500.  
  
 [  **@maxscans=** ] *max_scans*  
 Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала. *max_scans* — **int** значение по умолчанию 10.  
  
 [  **@continuous=** ] *непрерывного*  
 Указывает, следует ли хранимая процедура завершиться после выполнения одного цикла просмотра (0) или выполняться непрерывно, останавливаясь на паузу, заданную параметром *интервал_опроса* прежде чем выполнить повторно цикла просмотра (1). *непрерывные* — **tinyint** значение по умолчанию 0.  
  
 [  **@pollinginterval=** ] *интервал_опроса*  
 Число секунд между циклами просмотра журнала. *интервал_опроса* — **bigint** значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 sys.sp_cdc_scan вызывается внутри sys.sp_MScdc_capture_job Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание отслеживания агента используется системой отслеживания измененных данных. Эта процедура не может выполняться явно при операции сканирования журнала системы отслеживания измененных данных изменений уже активного или при включении базы данных для репликации транзакций. Эта хранимая процедура должна использоваться Администраторы, которые хотят настроить поведение автоматически настраиваемого задания отслеживания.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также:  
 [dbo.cdc_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
