---
title: sp_dbmmonitorupdate (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5b9c53913cc6f399109da7a84cd8ec7f68957a8b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760148"
---
# <a name="sp_dbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Обновляет таблицу состояний монитора зеркального отображения баз данных путем вставки новой строки для каждой зеркально отображенной базы данных, и усекает строки, срок хранения которых истек. По умолчанию срок хранения равен 7 дням (168 часам). При обновлении таблицы **sp_dbmmonitorupdate** оценивает метрики производительности.  
  
> [!NOTE]  
>  При первом запуске процедуры **sp_dbmmonitorupdate** создается таблица состояний зеркального отображения баз данных и предопределенная роль базы данных **dbm_monitor** в базе данных **msdb** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, для которой обновляется состояние зеркального отображения. Если *database_name* не указан, процедура обновляет таблицу состояния для каждой зеркально отображаемой базы данных на экземпляре сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Отсутствуют  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_dbmmonitorupdate** можно выполнять только в контексте базы данных **msdb** .  
  
 Если столбец таблицы состояний не применяется к роли участника, для этого участника значение равно NULL. Значение столбца также может быть равно NULL в случае недоступности нужных сведений, например в процессе отработки отказа или перезапуска сервера.  
  
 После того как **sp_dbmmonitorupdate** создает предопределенную роль базы данных **dbm_monitor** в базе данных **msdb** , члены предопределенной роли сервера **sysadmin** могут добавить любого пользователя к предопределенной роли базы данных **dbm_monitor** . Роль **dbm_monitor** позволяет своим членам просматривать состояние зеркального отображения базы данных, но не обновлять ее, но не может ни просматривать, ни настраивать события зеркального отображения базы данных.  
  
 При обновлении состояния зеркального отображения базы данных **sp_dbmmonitorupdate** проверяет Последнее значение метрики производительности зеркального отображения, для которой был указан порог предупреждения. Если значение превышает пороговое, процедура добавляет информационное событие в журнал событий. Все показатели являются средними значениями с момента последнего обновления. Дополнительные сведения см. в статье [Использование пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения (SQL Server)](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере состояние зеркального отображения обновляется только для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг &#40;SQL Server зеркального отображения базы данных&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
