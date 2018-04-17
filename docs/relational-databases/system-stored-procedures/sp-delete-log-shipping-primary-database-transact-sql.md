---
title: sp_delete_log_shipping_primary_database (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
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
- sp_delete_log_shipping_primary_database
- sp_delete_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_database
ms.assetid: cb1d5d00-2805-4d47-bd04-545232067345
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0583ca04a83e4abb4a815a7ac94eb3b0c99948b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletelogshippingprimarydatabase-transact-sql"></a>sp_delete_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура удаляет доставку журналов базы данных-источника, включая задания создания резервных копий, а также локальные и удаленные журналы. Эта хранимая процедура используется только после удаления баз данных-получателей с помощью **sp_delete_log_shipping_primary_secondary**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_log_shipping_primary_database  
[ @database = ] 'database'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@database =** ] "*базы данных*"  
 Имя базы данных-источника для доставки журналов. *База данных* — **sysname**, не имеет значения по умолчанию и не может иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_log_shipping_primary_database** должна запускаться из **master** базы данных на сервере-источнике. Эта хранимая процедура выполняет следующее:  
  
1.  удаляет задание создания резервных копий для указанной базы данных-источника;  
  
2.  Удаляет запись локального монитора в **log_shipping_monitor_primary** на основном сервере.  
  
3.  Удаляет соответствующие записи в **log_shipping_monitor_history_detail** и **log_shipping_monitor_error_detail**.  
  
4.  Если сервер мониторинга отличается от сервера-источника, удаляет запись монитора в **log_shipping_monitor_primary** на сервере мониторинга.  
  
5.  Удаляет соответствующие записи в **log_shipping_monitor_history_detail** и **log_shipping_monitor_error_detail** на сервере мониторинга.  
  
6.  Удаляет запись в **log_shipping_primary_databases** для этой базы данных-источника.  
  
7.  Вызовы **sp_delete_log_shipping_alert_job** на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 Этот пример иллюстрирует использование **sp_delete_log_shipping_primary_database** для удаления базы данных-источника **AdventureWorks2012**.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_database @database = N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
