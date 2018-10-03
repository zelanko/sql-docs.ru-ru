---
title: sp_refresh_log_shipping_monitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4382dc4de4010944e60cb37640759e91a0fc2727
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851562"
---
# <a name="sprefreshlogshippingmonitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данная хранимая процедура обновляет удаленные таблицы мониторинга последними данными с указанного сервера-источника или сервера-получателя для указанного агента отправки журналов. Эта процедура запускается только на сервере-источнике или сервере-получателе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@agent_id=** ] **"***agent_id***"**  
 Первичный идентификатор для резервирования или вторичный идентификатор для копирования или восстановления. *agent_id* — **uniqueidentifier** и не может иметь значение NULL.  
  
 [ **@agent_type=** ] **'***agent_type***'**  
 Тип задания доставки журналов:  
  
 0 = резервирование;  
  
 1 = копирование;  
  
 2 = восстановление.  
  
 *agent_type* — **tinyint** и не может иметь значение NULL.  
  
 [  **@database=** ] **"***базы данных***"**  
 База данных-источник или база данных-получатель, используемые для ведения журнала агентами резервного копирования или восстановления.  
  
 [ **@mode** ] *n*  
 Указывает необходимость обновления или очистки данных мониторинга. Тип данных *m* имеет тип tinyint и поддерживаемые значения:  
  
 1 = обновление (значение по умолчанию);  
  
 2 = delete  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 **sp_refresh_log_shipping_monitor** обновляет **log_shipping_monitor_primary**, **log_shipping_monitor_secondary**, **log_shipping_monitor_history_detail** , и **log_shipping_monitor_error_detail** таблицы данными сеанса, который еще не были перенесены. Это позволяет синхронизировать сервер мониторинга с сервером-источником или сервером-получателем, если в течение некоторого времени синхронизация не выполнялась. В дополнение к этому в случае необходимости разрешается очистка контрольных данных на сервере мониторинга.  
  
 **sp_refresh_log_shipping_monitor** должна запускаться из **master** базы данных на сервере первичной или вторичной.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
