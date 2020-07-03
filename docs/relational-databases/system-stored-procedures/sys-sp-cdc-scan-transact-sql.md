---
title: sys. sp_cdc_scan (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 558a2fd9ff62baa3448609eb42e5f31883fbac53
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891063"
---
# <a name="syssp_cdc_scan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @maxtrans = ] max_trans`Максимальное количество транзакций, обрабатываемых в каждом цикле просмотра. *max_trans* имеет **тип int** и значение по умолчанию 500.  
  
`[ @maxscans = ] max_scans`Максимальное число циклов просмотра, которое необходимо выполнить для извлечения всех строк из журнала. *max_scans* имеет **тип int** и значение по умолчанию 10.  
  
`[ @continuous = ] continuous`Указывает, должна ли хранимая процедура заканчиваться после выполнения одного цикла просмотра (0) или непрерывно работать, приостанавливаясь к времени, заданному *polling_interval* до повторного выполнения цикла просмотра (1). параметр *Continuous* имеет тип **tinyint** и значение по умолчанию 0.  
  
`[ @pollinginterval = ] polling_interval`Количество секунд между циклами просмотра журнала. *polling_interval* имеет тип **bigint** и значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 sys. sp_cdc_scan вызывается внутренне посредством sys. sp_MScdc_capture_job, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Задание отслеживания агента используется системой отслеживания измененных данных. Процедура не может быть выполнена явным образом, если активна операция просмотра журнала системы отслеживания измененных данных или в базе данных включена репликация транзакций. Эта хранимая процедура должна использоваться администраторами, которым необходимо настроить действие задания отслеживания, настроенное автоматически.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
