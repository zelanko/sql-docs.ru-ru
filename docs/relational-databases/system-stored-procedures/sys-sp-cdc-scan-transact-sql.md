---
title: sys.sp_cdc_scan (Transact-SQL) | Документация Майкрософт
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1e7651c6df4a277d72a71c0cdb8a5910ae19ba76
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536786"
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
`[ @maxtrans = ] max_trans` Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра. *max_trans* — **int** значение по умолчанию 500.  
  
`[ @maxscans = ] max_scans` Максимальное число циклов просмотра, выполняемых для извлечения всех строк из журнала. *max_scans* — **int** значение по умолчанию 10.  
  
`[ @continuous = ] continuous` Указывает, следует ли хранимая процедура завершиться после выполнения одного цикла просмотра (0) или выполняться непрерывно, времени, заданного параметром *polling_interval* перед останавливаясь цикла просмотра (1). *Непрерывная* — **tinyint** значение по умолчанию 0.  
  
`[ @pollinginterval = ] polling_interval` Число секунд между циклами просмотра журнала. *polling_interval* — **bigint** значение по умолчанию 0.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 sys.sp_cdc_scan можно вызвать изнутри с sys.sp_MScdc_capture_job Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание отслеживания агента используется системой отслеживания измененных данных. Невозможно выполнить процедуру явным образом, если уже активна операция просмотра журнала системы отслеживания измененных данных средства изменений или базе данных включена для репликации транзакций. Эта хранимая процедура должна использоваться администраторами, которым необходимо настроить поведение автоматически настраиваемого задания отслеживания.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="see-also"></a>См. также  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
