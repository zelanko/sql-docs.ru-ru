---
title: Контролировать загрузку для Parallel Data Warehouse | Документация Майкрософт
description: Отслеживание активные и Недавние загрузок с помощью консоли администрирования (APS) системы платформы аналитики или параллельных данных (PDW) системные представления.»
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cb840c64c2235a2f3902c45633aa5471655482dc
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52413521"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Монитор загружает в Parallel Data Warehouse
Монитор, активные и Недавние [dwloader](dwloader.md) загружает с помощью консоли администрирования Analytics Platform System (APS) или Parallel Data Warehouse (PDW) [системных представлений](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/). 
  
> [!TIP]  
> Некоторые загружает инициируется с помощью инструкций INSERT или средства бизнес-аналитики, с помощью инструкций SQL для выполнения загрузки. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>предварительные требования  
Независимо от того, метод, используемый для наблюдения за нагрузкой имя входа должно иметь разрешение на доступ к базовым источникам данных. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Мониторинг загрузки  
Как контролировать загрузку в следующих разделах.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Чтобы контролировать загрузку с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  В верхнем меню щелкните **загружает**. Вы увидите сортируемого таблица, показывающая всех последних и активных нагрузок, а также дополнительные сведения, например нагрузки завершена ли по-прежнему активна. Щелкните заголовки столбцов для сортировки строк.  
  
3.  Чтобы просмотреть дополнительные сведения для определенной нагрузки, нажмите кнопку загрузки **идентификатор** в левом столбце. В подробном представлении вы увидите ход выполнения каждого шага нагрузки.  
  
См. приведенные далее системные представления сведения метаданных о нагрузке, которое отображается в консоли администрирования:  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Чтобы контролировать загрузку с помощью системных представлений  
Чтобы отслеживать активные и Недавние загрузки с помощью представлений SQL Server PDW, выполните следующие действия. Каждый используется системное представление см. в документации для этого представления сведения в столбцах и потенциальных значений, возвращенных представлением.  
  
1.  Найти `request_id` для загрузки в [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) представления путем поиска загрузчика командной строки в `command` столбец для этого представления.  
  
    Например, следующая команда возвращает текущее состояние и текст команды, а также `request_id`.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Используйте `request_id` для получения дополнительных сведений для загрузки с помощью [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) , и [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) представления. Например, следующий запрос возвращает `run_id` и сведения о начала, окончания и длительность времени загрузки, а также все ошибки и на количество обработанных строк:  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id='12738';  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
