---
title: DBCC SQLPERF (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQLPERF
- DBCC_SQLPERF_TSQL
- SQLPERF_TSQL
- DBCC SQLPERF
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], transaction logs
- transaction logs [SQL Server], space usage
- space [SQL Server], transaction logs
- DBCC SQLPERF statement
ms.assetid: ec9225ce-e20f-4b03-8b3a-7bcad8a649df
author: pmasl
ms.author: umajay
ms.openlocfilehash: 8cb409823bad1370c38b6dc99f04c7e49d58796a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "73982410"
---
# <a name="dbcc-sqlperf-transact-sql"></a>DBCC SQLPERF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Выдает статистику использования места, занятого журналом транзакций на диске, для всех баз данных. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это может применяться для сброса статистики кратковременных блокировок и ожидания.
  
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и выше), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([предварительная версия в некоторых регионах](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```
DBCC SQLPERF   
(  
     [ LOGSPACE ]  
     | [ "sys.dm_os_latch_stats" , CLEAR ]  
     | [ "sys.dm_os_wait_stats" , CLEAR ]  
)   
     [WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
LOGSPACE  
Возвращает текущий размер журнала транзакций и процент пространства журнала, используемого для каждой базы данных. С помощью этих данных можно контролировать используемое пространство в журнале транзакций.

> [!IMPORTANT]
> Дополнительные сведения об использовании пространства для журнала транзакций начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] см. в разделе [Примечания](#Remarks) в этой статье.
  
**"sys.dm_os_latch_stats"** , CLEAR  
Сбрасывает статистику кратковременных блокировок. Дополнительные сведения см. в разделе [sys.dm_os_latch_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md). Этот параметр не доступен в среде [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
**"sys.dm_os_wait_stats"** , CLEAR  
Сбрасывает статистику ожидания. Дополнительные сведения см. в разделе [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). Этот параметр не доступен в среде [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
WITH NO_INFOMSGS  
Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="result-sets"></a>Результирующие наборы  
 В следующей таблице отображены столбцы результирующего набора.  
  
|Имя столбца|Определение|  
|---|---|
|**Имя базы данных**|Имя базы данных, которой соответствует отображаемая статистика журнала.|  
|**Log Size (MB)**|Текущий размер, выделенный для журнала. Этот значение всегда меньше объема, исходно выделенного для журнала, так как компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] резервирует небольшую часть места на диске для внутренних данных заголовка.|  
|**Log Space Used (%)**|Доля (в процентах) файла журнала, используемого для хранения сведений журнала транзакций.|  
|**Состояние**|Состояние файла журнала. Всегда равно 0.|  
  
## <a name="remarks"></a><a name="Remarks"></a> Замечания  
Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] используйте динамическое административное представление [sys.dm_db_log_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)`DBCC SQLPERF(LOGSPACE)` для просмотра сведений об использовании пространства для журнала транзакций в каждой базе данных.    
 
В журнале транзакций записывается каждая транзакция, выполненная в базе данных. Дополнительные сведения см. в разделах [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md) и [Руководство по архитектуре журнала транзакций SQL Server и управлению им](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md).
  
## <a name="permissions"></a>Разрешения  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для запуска `DBCC SQLPERF(LOGSPACE)` требуется разрешение `VIEW SERVER STATE` на сервер. Для сброса статистики кратковременных блокировок и ожидания необходимо разрешение `ALTER SERVER STATE` на сервер.
  
В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] для уровней "Премиум" и "Критически важный для бизнеса" необходимо разрешение `VIEW DATABASE STATE` в базе данных. В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] для уровней "Стандартный", "Базовый" и "Общего назначения" требуется учетная запись администратора [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Сброс статистики кратковременных блокировок и ожидания не поддерживаются.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-log-space-information-for-all-databases"></a>A. Вывод сведений о пространстве журнала для всех баз данных  
В следующем примере выводятся сведения `LOGSPACE` для всех баз данных, содержащихся в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
```sql  
DBCC SQLPERF(LOGSPACE);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Database Name Log Size (MB) Log Space Used (%) Status        
------------- ------------- ------------------ -----------   
master         3.99219      14.3469            0   
tempdb         1.99219      1.64216            0   
model          1.0          12.7953            0   
msdb           3.99219      17.0132            0   
AdventureWorks 19.554688    17.748701          0  
```  
  
### <a name="b-resetting-wait-statistics"></a>Б. Сброс статистики ожидания  
В следующем примере сбрасывается статистика ожидания для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
```sql  
DBCC SQLPERF("sys.dm_os_wait_stats",CLEAR);  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)   
[sys.dm_os_latch_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)    
[sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
[sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)    
[sys.dm_db_log_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
[sys.dm_db_log_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)     
[sys.dm_db_log_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)     

