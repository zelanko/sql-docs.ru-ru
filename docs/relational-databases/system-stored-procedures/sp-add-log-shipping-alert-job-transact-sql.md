---
description: sp_add_log_shipping_alert_job (Transact-SQL)
title: sp_add_log_shipping_alert_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_alert_job_TSQL
- sp_add_log_shipping_alert_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_alert_job
ms.assetid: dd95d96e-8963-4aa9-bdcc-3e4b1bc002d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b5c872f0346cce50ff27e442991efa5e5f4e4391
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464722"
---
# <a name="sp_add_log_shipping_alert_job-transact-sql"></a>sp_add_log_shipping_alert_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Эта хранимая процедура проверяет, было ли создано на сервере задание предупреждения. Если задание предупреждения не существует, эта хранимая процедура создает задание предупреждения и добавляет его идентификатор задания в **log_shipping_monitor_alert** таблицу. По умолчанию, это задание предупреждения включено и запускается по расписанию каждые две минуты.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_log_shipping_alert_job  
[, [ @alert_job_id = ] alert_job_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @alert_job_id = ] alert_job_id OUTPUT`[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Идентификатор задания агента для задания предупреждения доставки журналов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_log_shipping_alert_job** должны быть запущены из базы данных **master** на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано выполнение **sp_add_log_shipping_alert_job** для создания идентификатора задания предупреждения.  
  
```  
USE master  
GO  
EXEC sp_add_log_shipping_alert_job;  
```  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
