---
title: sys.sp_cdc_scan (Transact-SQL) | Документы Microsoft
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
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b143e1ee7642774ae08ddd685a6c3fc6b641180f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
