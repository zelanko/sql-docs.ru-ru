---
title: sp_cleanup_log_shipping_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cleanup_log_shipping_history_TSQL
- sp_cleanup_log_shipping_history
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cleanup_log_shipping_history
ms.assetid: 96d236a9-1d0e-4f83-a4d3-f825b7381e46
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 091cdede60229e70fd492043db0cdfc3ab8cfb7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771285"
---
# <a name="sp_cleanup_log_shipping_history-transact-sql"></a>sp_cleanup_log_shipping_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Эта хранимая процедура производит чистку журнала локально и на сервере мониторинга, в зависимости от срока хранения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cleanup_log_shipping_history  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @agent_id = ] 'agent_id',`Основной идентификатор резервной копии или вторичный идентификатор для копирования или восстановления. *agent_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @agent_type = ] 'agent_type'`Тип задания доставки журналов. 0 = резервное копирование, 1 = копирование, 2 = восстановление. *agent_type* имеет тип **tinyint** и не может иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 **sp_cleanup_log_shipping_history** должны запускаться из базы данных **master** на любом сервере доставки журналов. Эта хранимая процедура очищает локальные и удаленные копии **log_shipping_monitor_history_detail** и **log_shipping_monitor_error_detail** на основе срока хранения журнала.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
