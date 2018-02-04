---
title: "sp_dbmmonitorupdate (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorupdate
- sp_dbmmonitorupdate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorupdate
- database mirroring [SQL Server], monitoring
ms.assetid: 9ceb9611-4929-44ee-a406-c39ba2720fd5
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2970c0c6f75755e295fae32a1a5ceab046bb75d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spdbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет таблицу состояний монитора зеркального отображения баз данных путем вставки новой строки для каждой зеркально отображенной базы данных, и усекает строки, срок хранения которых истек. По умолчанию срок хранения равен 7 дням (168 часам). При обновлении таблицы, **sp_dbmmonitorupdate** оценивает метрики производительности.  
  
> [!NOTE]  
>  В первый раз **sp_dbmmonitorupdate** запускается, он создает таблицы состояния зеркального отображения базы данных и **dbm_monitor** предопределенной роли базы данных в **msdb** базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, для которой обновляется состояние зеркального отображения. Если *имя_базы_данных* не указан, процедура обновляет таблицу состояний для каждой зеркальной базы данных на экземпляре сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 **sp_dbmmonitorupdate** может выполняться только в контексте **msdb** базы данных.  
  
 Если столбец таблицы состояний не применяется к роли участника, для этого участника значение равно NULL. Значение столбца также может быть равно NULL в случае недоступности нужных сведений, например в процессе отработки отказа или перезапуска сервера.  
  
 После **sp_dbmmonitorupdate** создает **dbm_monitor** предопределенной роли базы данных в **msdb** базы данных, члены **sysadmin** предопределенной роли сервера может добавить любого пользователя в **dbm_monitor** предопределенной роли базы данных. **Dbm_monitor** роль дает возможность ее членам просмотреть состояние зеркального отображения базы данных, но не обновления, но не Просмотр и настройка событий зеркального отображения базы данных.  
  
 При обновлении состояния зеркального отображения базы данных, **sp_dbmmonitorupdate** изучает последние значения метрик производительности зеркального отображения для которого был указан порог предупреждения. Если значение превышает пороговое, процедура добавляет информационное событие в журнал событий. Все показатели являются средними значениями с момента последнего обновления. Дополнительные сведения см. в статье [Использование пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения (SQL Server)](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере состояние зеркального отображения обновляется только для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
