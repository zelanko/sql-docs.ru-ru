---
title: Неподдерживаемые функции ядра СУБД в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fc6b593694feda96032cb0af45d9b3bdb4cc2a8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779880"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a>Неподдерживаемые функции ядра СУБД в SQL Server 2014
  В этом разделе описаны функции компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , которые больше не доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 В следующей таблице перечислены функции, которые были исключены из [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
|Category|Неподдерживаемая функция|Замена|  
|--------------|--------------------------|-----------------|  
|Уровень совместимости|Уровень совместимости 90|Уровень совместимости базы данных должен быть не менее 100. При обновлении базы данных с уровнем совместимости менее 100 до версии [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]во время операции обновления для этой базы данных устанавливается уровень совместимости 100.|  
  
## <a name="discontinued-features-in-includesssql11includessssql11-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 В следующей таблице перечислены функции, которые были исключены из [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
|Category|Неподдерживаемая функция|Замена|  
|--------------|--------------------------|-----------------|  
|Резервное копирование и восстановление|**Резервное копирование {базы данных &#124; LOG} WITH PASSWORD** и **резервной копии {базы данных &#124; LOG} WITH MEDIAPASSWORD** не поддерживаются. **ВОССТАНОВИТЬ {базы данных &#124; ЖУРНАЛА} с [MEDIA] PASSWORD**остается устаревшей.|None|  
|Резервное копирование и восстановление|**RESTORE {DATABASE &AMP;#124; ЖУРНАЛА}... WITH DBO_ONLY**|**RESTORE {DATABASE &AMP;#124; ЖУРНАЛА}...... С ПОМОЩЬЮ RESTRICTED_USER**|  
|Уровень совместимости|уровень совместимости 80|Уровень совместимости базы данных должен быть не менее 90.|  
|Параметры конфигурации|`sp_configure 'user instance timeout'` и `'user instances enabled'`|Использование функции локальной базы данных. Дополнительные сведения см. в разделе [программа SqlLocalDB](../tools/sqllocaldb-utility.md)|  
|Протоколы соединений|Прекращена поддержка протокола VIA.|Используйте вместо него протокол TCP.|  
|Объекты базы данных|Предложение `WITH APPEND` в триггерах|Создайте заново весь триггер.|  
|Параметры базы данных|`sp_dboption`|`ALTER DATABASE`|  
|Mail|Служба SQL Mail|Использование компонента Database Mail. Подробные сведения см. в разделах [Database Mail](../relational-databases/database-mail/database-mail.md) и  [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).|  
|Управление памятью|Поддержка 32-разрядных расширений AWE и памяти с «горячей» заменой в 32-разрядных системах.|Используйте 64-разрядную операционную систему.|  
|Метаданные|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|Программирование|Объекты SQL-DMO|Управляющие объекты SQL Server (SMO)|  
|Указания запросов|Подсказка `FASTFIRSTROW`|`OPTION (FAST` *n* `)`.|  
|Удаленные серверы|Пользователям больше не предоставляется возможность создавать новые удаленные серверы с помощью хранимой процедуры `sp_addserver`. Хранимая процедура `sp_addserver` с параметром local остается доступной. Можно использовать удаленные серверы, которые сохраняются при обновлении или были созданы при репликации.|Замените удаленные серверы связанными серверами.|  
|безопасность|`sp_dropalias`|Псевдонимы заменены сочетанием учетных записей пользователей и ролями базы данных. Удалите псевдонимы в обновленных базах данных с помощью хранимой процедуры `sp_dropalias`.|  
|безопасность|Параметр версии **PWDCOMPARE** , представляющий значение имени входа из более ранних версий, чем [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000, более не поддерживается.|None|  
|Возможности объектов SMO по программированию компонента Service Broker|Класс **Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** больше не реализует интерфейс **Microsoft.SqlServer.Management.Smo.IObjectPermission** .||  
|Параметры SET|`SET DISABLE_DEF_CNST_CHK`|Нет.|  
|Системные таблицы|sys.database_principal_aliases|Использование ролей вместо псевдонимов.|  
|Transact-SQL|Параметр `RAISERROR`, представленный в формате `RAISERROR integer 'string'`, более не поддерживается.|Перепишите инструкцию с использованием текущего **RAISERROR(...)**  синтаксис.|  
|синтаксис Transact-SQL|`COMPUTE / COMPUTE BY`|Используйте `ROLLUP`.|  
|синтаксис Transact-SQL|Использование **\* =** и **=&#42;**|Использование синтаксиса соединения ANSI. Дополнительные сведения см. в разделе [FROM (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)|  
|XEvents|databases_data_file_size_changed databases_log_file_size_changed<br /><br /> eventdatabases_log_file_used_size_changed<br /><br /> locks_lock_timeouts_greater_than_0<br /><br /> locks_lock_timeouts|Заменены событие database_file_size_change, database_file_size_change<br /><br /> database_file_size_change event<br /><br /> lock_timeout_greater_than_0<br /><br /> lock_timeout|  
  
 **Дополнительные изменения XEvent**  
  
 **resource_monitor_ring_buffer_record**:  
  
-   Удалены поля: single_pages_kb, multiple_pages_kb  
  
-   Добавлены поля: target_kb, pages_kb  
  
 **memory_node_oom_ring_buffer_recorded**:  
  
-   Удалены поля: single_pages_kb, multiple_pages_kb  
  
-   Добавлены поля: target_kb, pages_kb  
  
## <a name="see-also"></a>См. также  
 [Нерекомендуемые функции ядра СУБД в SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
