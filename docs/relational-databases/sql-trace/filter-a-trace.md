---
title: "Фильтрация трассировки | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- events [SQL Server], filters
- filters [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 019c10ab-68f6-4e40-a5e8-735b2e1270db
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49755f29a54164f008e19bc542a9ca650e54b37b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="filter-a-trace"></a>Фильтрация трассировки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Фильтры ограничивают сбор событий в трассировке. Если фильтр не установлен, то на выход трассировки возвращаются все события выбранных классов событий. Например, ограничение в трассировке по отслеживанию только имен определенных пользователей Windows сокращает объем выходных данных до объема данных только для этих пользователей.  
  
 Установка фильтра трассировки необязательна. Однако фильтр уменьшает дополнительную нагрузку, возникающую при трассировке. Фильтр возвращает конкретные данные, тем самым упрощая аудит и анализ производительности.  
  
 Для фильтрации данных о событии, зафиксированных во время трассировки, выберите критерий события трассировки, который будет возвращать из трассировки только необходимые данные. Например, можно включить или выключить мониторинг активности определенного приложения в трассировке.  
  
> [!NOTE]  
>  Когда программа [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] создает трассировку, по умолчанию производится фильтрация своей собственной активности.  
  
 Рассмотрим другой пример: если производится мониторинг запросов для определения пакетов, которым для выполнения требуется наибольшее время, то нужно установить критерий событий трассировки для проведения мониторинга только тех пакетов, выполнение которых проходит дольше 30 секунд (минимальное значение процессорного времени равно 30 000 миллисекунд).  
  
## <a name="filter-creation-guidelines"></a>Правила создания фильтров  
 В общем случае для создания фильтра трассировки выполните следующие шаги.  
  
1.  Определите события, которые нужно включить в трассировку.  
  
2.  Определите данные и столбцы данных, содержащие необходимые сведения.  
  
3.  Определите подмножество необходимых данных и определите фильтры, основанные на данном подмножестве.  
  
 Допустим, что интересны только те события, которые происходят дольше определенного отрезка времени. Тогда можно создать трассировку, в которой будут содержаться события, для которых значения столбца данных **Продолжительность** больше, чем 300 миллисекунд. В трассировку не будут включаться события, выполнение которых продолжалось менее 300 миллисекунд.  
  
 Создавать фильтры можно при помощи хранимых процедур Transact-SQL или приложения SQL Server Profiler.  
  
 **Фильтрация событий в шаблоне трассировки**  
  
 [Фильтрация событий в трассировке (SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
 [Создание фильтра трассировки (Transact-SQL)](../../relational-databases/sql-trace/set-a-trace-filter-transact-sql.md)  
  
 **Изменение фильтров**  
  
 [Изменение фильтра (SQL Server Profiler)](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
 Доступность фильтра зависит от столбца данных. По некоторым столбцам данных нельзя проводить фильтрацию. Для столбцов данных, по которым можно проводить фильтрацию, она возможна только с помощью специальных реляционных операторов, как показано в следующей таблице.  
  
|Реляционный оператор|Символ оператора|Описание|  
|-------------------------|---------------------|-----------------|  
|Похоже|Похоже|Определяет, что данные событий трассировки должны быть похожи на введенный текст. Допускает множественные значения.|  
|Не похоже|Не похоже|Определяет то, что данные событий трассировки не должны быть похожи на введенный текст. Допускает множественные значения.|  
|Равно|=|Определяет то, что данные событий трассировки должны быть равны введенному значению. Допускает множественные значения.|  
|Не равно|<>|Определяет то, что данные событий трассировки не должны быть равны введенному значению. Допускает множественные значения.|  
|Больше чем|>|Определяет то, что данные событий трассировки должны быть больше чем введенное значение.|  
|Больше или равно|>=|Определяет то, что данные событий трассировки должны быть больше или равны введенному значению.|  
|Меньше чем|<|Определяет то, что данные событий трассировки должны быть меньше чем введенное значение.|  
|Меньше или равно|<=|Определяет то, что данные событий трассировки должны быть меньше или равны введенному значению.|  
  
 В следующей таблице приведен список фильтруемых столбцов данных и доступных реляционных операторов.  
  
|Столбцы данных|Реляционные операторы|  
|------------------|--------------------------|  
|**ApplicationName**|LIKE, NOT LIKE|  
|**BigintData1**|=, <>, >=, <=|  
|**BigintData2**|=, <>, >=, <=|  
|**BinaryData**|С помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отфильтруйте события в этом столбце данных. Дополнительные сведения см. в разделе [Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**ClientProcessID**|=, <>, >=, <=|  
|**ColumnPermissions**|=, <>, >=, <=|  
|**ЦП**|=, <>, >=, <=|  
|**DatabaseID**|=, <>, >=, <=|  
|**DatabaseName**|LIKE, NOT LIKE|  
|**DBUserName**|LIKE, NOT LIKE|  
|**Длительность**|=, <>, >=, \<=|  
|**EndTime**|>=, <=|  
|**Ошибка**|=, <>, >=, <=|  
|**EventSubClass**|=, <>, >=, <=|  
|**FileName**|LIKE, NOT LIKE|  
|**GUID**|С помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отфильтруйте события в этом столбце данных. Дополнительные сведения см. в разделе [Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**Дескриптор**|=, <>, >=, <=|  
|**HostName**|LIKE, NOT LIKE|  
|**IndexID**|=, <>, >=, <=|  
|**IntegerData**|=, <>, >=, <=|  
|**IntegerData2**|=, <>, >=, <=|  
|**IsSystem**|=, <>, >=, <=|  
|**LineNumber**|=, <>, >=, <=|  
|**LinkedServerName**|LIKE, NOT LIKE|  
|**LoginName**|LIKE, NOT LIKE|  
|**LoginSid**|С помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отфильтруйте события в этом столбце данных. Дополнительные сведения см. в разделе [Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**MethodName**|LIKE, NOT LIKE|  
|**Режим**|=, <>, >=, <=|  
|**NestLevel**|=, <>, >=, <=|  
|**NTDomainName**|LIKE, NOT LIKE|  
|**NTUserName**|LIKE, NOT LIKE|  
|**ObjectID**|=, <>, >=, <=|  
|**ObjectID2**|=, <>, >=, <=|  
|**ObjectName**|LIKE, NOT LIKE|  
|**ObjectType**|=, <>, >=, <=|  
|**Offset**|=, <>, >=, <=|  
|**OwnerID**|=, <>, >=, <=|  
|**OwnerName**|LIKE, NOT LIKE|  
|**ParentName**|LIKE, NOT LIKE|  
|**Разрешения**|=, <>, >=, <=|  
|**ProviderName**|LIKE, NOT LIKE|  
|**Reads**|=, <>, >=, <=|  
|**RequestID**|=, <>, >=, <=|  
|**RoleName**|LIKE, NOT LIKE|  
|**RowCounts**|=, <>, >=, <=|  
|**SessionLoginName**|LIKE, NOT LIKE|  
|**Severity**|=, <>, >=, <=|  
|**SourceDatabaseID**|=, <>, >=, <=|  
|**SPID**|=, <>, >=, \<=|  
|**SqlHandle**|С помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отфильтруйте события в этом столбце данных. Дополнительные сведения см. в разделе [Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**StartTime**|>=, <=|  
|**Состояние**|=, <>, >=, <=|  
|**Успешно**|=, <>, >=, <=|  
|**TargetLoginName**|LIKE, NOT LIKE|  
|**TargetLoginSid**|С помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отфильтруйте события в этом столбце данных. Дополнительные сведения см. в разделе [Фильтрация трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**TargetUserName**|LIKE, NOT LIKE|  
|**TextData** *|LIKE, NOT LIKE|  
|**TransactionID**|=, <>, >=, <=|  
|**Тип**|=, <>, >=, <=|  
|**Writes**|=, <>, >=, <=|  
|**XactSequence**|=, <>, >=, <=|  
  
 \* Если события трассируются из программы **osql** или **sqlcmd** , то всегда добавляйте **%** к фильтрам для столбца данных **TextData** .  
  
 В целях предосторожности трассировка SQL автоматически исключает из трассировки любые сведения о хранимых процедурах безопасности, затрагивающих пароли. Этот механизм безопасности работает всегда и его нельзя настроить. Он предотвращает перехват паролей пользователями, получившими другим способом доступ к трассировке работы всех служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 За следующими хранимыми процедурами безопасности осуществляется контроль, но в столбец данных **TextData** выходные данные не записываются:  
  
 [sp_addapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)  
  
 [sp_adddistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)  
  
 [sp_adddistributiondb (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)  
  
 [sp_adddistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)  
  
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
 [sp_addlinkedsrvlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)  
  
 [sp_addlogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)  
  
 [sp_addmergepullsubscription_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)  
  
 [sp_addpullsubscription_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
 [sp_addremotelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
 [sp_addsubscriber (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)  
  
 [sp_approlepassword (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-approlepassword-transact-sql.md)  
  
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)  
  
 [sp_changesubscriber (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)  
  
 [sp_dsninfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)  
  
 [sp_helpsubscription_properties (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
 [sp_link_publication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)  
  
 [sp_password (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md)  
  
 [sp_setapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)  
  
  
