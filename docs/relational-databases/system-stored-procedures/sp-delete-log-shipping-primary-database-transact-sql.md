---
title: sp_delete_log_shipping_primary_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_primary_database
- sp_delete_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_database
ms.assetid: cb1d5d00-2805-4d47-bd04-545232067345
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aff19eabc5738e986fca1bf13f85130daead3217
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909868"
---
# <a name="sp_delete_log_shipping_primary_database-transact-sql"></a>sp_delete_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура удаляет доставку журналов базы данных-источника, включая задания создания резервных копий, а также локальные и удаленные журналы. Используйте эту хранимую процедуру только после удаления баз данных-получателей с помощью **sp_delete_log_shipping_primary_secondary**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_log_shipping_primary_database  
[ @database = ] 'database'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database'` — это имя базы данных-источника для доставки журналов. *база данных* имеет тип **sysname**, не имеет значения по умолчанию и не может иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Отсутствуют.  
  
## <a name="remarks"></a>Remarks  
 **sp_delete_log_shipping_primary_database** должны быть запущены из базы данных **master** на сервере источника. Эта хранимая процедура выполняет следующее:  
  
1.  удаляет задание создания резервных копий для указанной базы данных-источника;  
  
2.  Удаляет запись локального монитора в **log_shipping_monitor_primary** на сервере источника.  
  
3.  Удаляет соответствующие записи в **log_shipping_monitor_history_detail** и **log_shipping_monitor_error_detail**.  
  
4.  Если сервер мониторинга отличается от сервера-источника, удаляет запись монитора в **log_shipping_monitor_primary** на сервере мониторинга.  
  
5.  Удаляет соответствующие записи в **log_shipping_monitor_history_detail** и **log_shipping_monitor_error_detail** на сервере мониторинга.  
  
6.  Удаляет запись в **log_shipping_primary_databases** для этой базы данных источника.  
  
7.  Вызывает **sp_delete_log_shipping_alert_job** на сервере мониторинга.  

## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В этом примере показано использование **sp_delete_log_shipping_primary_database** для удаления **AdventureWorks2012**базы данных источника.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_database @database = N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>См. также статью  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
