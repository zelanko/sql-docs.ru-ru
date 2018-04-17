---
title: sp_dbmmonitorresults (Transact-SQL) | Документы Microsoft
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
- sp_dbmmonitorresults
- sp_dbmmonitorresults_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorresults
- database mirroring [SQL Server], monitoring
ms.assetid: d575e624-7d30-4eae-b94f-5a7b9fa5427e
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfa798863af2c43f00908accf30c8d03c06202f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spdbmmonitorresults-transact-sql"></a>sp_dbmmonitorresults (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строки состояния для просматриваемой базы данных из таблицы состояний, в которой сохранен журнал мониторинга зеркального отображения базы данных, а также позволяет выбрать, будет ли процедура получать последнее состояние заранее.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorresults database_name   
   , rows_to_return  
    , update_status   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Указывает базу данных, для которой нужно вернуть состояние зеркального отображения.  
  
 *rows_to_return*  
 Указывает количество возвращенных строк:  
  
 0 = последняя строка  
  
 1 = строки за последние два часа  
  
 2 = строки за последние четыре часа  
  
 3 = строки за последние восемь часов  
  
 4 = строки за последний день  
  
 5 = строки за последние два дня  
  
 6 = последние 100 строк  
  
 7 = 500 последней строки  
  
 8 = последние 1 000 строк  
  
 9 = последние 1 000 000 строк  
  
 *update_status*  
 Указывает перед возвратом процедурой результатов:  
  
 0 = состояние базы данных не обновлено. Результаты вычислены с помощью последних двух строк, возраст которых зависит от того, когда была обновлена таблица состояния.  
  
 1 = обновляет состояние базы данных, вызвав **sp_dbmmonitorupdate** перед вычислением результатов. Тем не менее, если таблица состояния была обновлена в предыдущие 15 секунд или пользователь не является членом **sysadmin** предопределенной роли сервера **sp_dbmmonitorresults** выполняется без обновления состояния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает запрашиваемое количество строк журнала состояния для указанной базы данных. Каждая строка содержит следующие сведения:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Имя зеркальной базы данных.|  
|**Роли**|**int**|Текущая роль экземпляра сервера в зеркальном отображения:<br /><br /> 1 = основная;<br /><br /> 2 = зеркальная;|  
|**mirroring_state**|**int**|Состояние базы данных:<br /><br /> 0 = приостановлено;<br /><br /> 1 = отключено<br /><br /> 2 = идет процесс синхронизации;<br /><br /> 3 = ожидание отработки отказа;<br /><br /> 4 = синхронизирована;|  
|**witness_status**|**int**|Состояние соединения свидетеля в сеансе зеркального отображения базы данных, может быть:<br /><br /> 0 = неизвестное состояние;<br /><br /> 1 = подключен;<br /><br /> 2 = отключен;|  
|**log_generation_rate**|**int**|Объем сформированного файла журнала, с момента с предыдущего обновления состояния зеркального отображения текущей базы данных, в килобайтах в секунду.|  
|**unsent_log**|**int**|Размер неотправленного журнала в очереди на основном сервере в килобайтах.|  
|**send_rate**|**int**|Скорость отправки журнала с основного сервера на зеркальный, в килобайтах в секунду.|  
|**unrestored_log**|**int**|Размер очереди повтора на зеркальном сервере, в килобайтах.|  
|**recovery_rate**|**int**|Частота повторов на зеркальном сервере, в килобайтах в секунду.|  
|**transaction_delay**|**int**|Общая задержка обработки всех транзакций, в миллисекундах.|  
|**transactions_per_sec**|**int**|Количество транзакций в секунду, которые встречаются на экземпляре основного сервера.|  
|**average_delay**|**int**|Средняя задержка на экземпляре основного сервера для каждой транзакции из-за зеркального отображения базы данных. В режиме высокой производительности (когда свойство SAFETY имеет значение OFF), это значение равно 0.|  
|**time_recorded**|**datetime**|Время, за которое строка была записана монитором зеркального отображения баз данных. Это системное время основного сервера.|  
|**time_behind**|**datetime**|Приблизительное системное время основного сервера, с которым синхронизирована зеркальная база данных. Это значение имеет смысл только на экземпляре основного сервера.|  
|**local_time**|**datetime**|Значение системного времени на локальном экземпляре сервера, когда эта строка была обновлена.|  
  
## <a name="remarks"></a>Замечания  
 **sp_dbmmonitorresults** может выполняться только в контексте **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли сервера или в **dbm_monitor** предопределенной роли базы данных в **msdb** базы данных. **Dbm_monitor** роль дает возможность ее членам просмотреть состояние зеркального отображения базы данных, но не обновления, но не Просмотр и настройка событий зеркального отображения базы данных.  
  
> [!NOTE]  
>  При первой **sp_dbmmonitorupdate** выполняется, он создает **dbm_monitor** предопределенной роли базы данных в **msdb** базы данных. Члены **sysadmin** предопределенной роли сервера может добавить любого пользователя в **dbm_monitor** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает строки, записанные в течение последних двух часов, без обновления состояния базы данных.  
  
```  
USE msdb;  
EXEC sp_dbmmonitorresults AdventureWorks2012, 2, 0;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorupdate (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql.md)  
  
  
