---
title: Контролировать загрузку для параллельного хранилища данных | Документы Microsoft
description: Контролировать загрузку активных и последние с помощью консоли администрирования System (APS) Analytics платформы или параллельных системные представления (PDW) данные хранилища.»
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8980259b69dfa74c2bb27c9406553a5b5810348a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585676"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Монитор загружает в параллельное хранилище данных
Монитор активных и последние [dwloader](dwloader.md) загружается с помощью консоли администрирования Analytics Platform System (APS) или параллельного хранилища данных (PDW) [системных представлений](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/). 
  
> [!TIP]  
> Некоторые загружает инициируется с помощью инструкций INSERT или средств бизнес-аналитики, в которых применяются инструкции SQL для выполнения загрузки. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>предварительные требования  
Независимо от того, метод, используемый для наблюдения за нагрузкой имя входа должно иметь разрешение на доступ к базовым источникам данных. 

<!-- MISSING LINKS
For the permissions to grant, see “Use All of the Admin Console” in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Мониторинг загрузки  
В следующих разделах описаны способы мониторинга нагрузки.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Чтобы контролировать загрузку с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  В верхнем меню щелкните **загружает**. Вы увидите сортируемого таблица, в которой все последние и активных нагрузок, а также дополнительные сведения, например нагрузки завершена ли по-прежнему активна. Щелкните заголовки столбцов для сортировки строк.  
  
3.  Для просмотра дополнительных сведений для конкретных нагрузки, нажмите кнопку загрузки **идентификатор** в левом столбце. В подробном представлении вы увидите ход выполнения каждого шага нагрузки.  
  
См. следующие системные представления сведения метаданных о нагрузку, которая отображается в консоли администрирования:  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Чтобы контролировать загрузку с помощью системных представлений  
Для наблюдения за active и последних загрузок с помощью представлений SQL Server PDW, выполните следующие действия. Для каждого системного представления используются см. в документации для этого представления сведения в столбцах и потенциальных значений, возвращенных представлением.  
  
1.  Найти `request_id` для загрузки в [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) представления, который можно найти загрузчик командной строки в `command` столбец для этого представления.  
  
    Например, следующая команда возвращает текущее состояние и текст команды, а также `request_id`.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Используйте `request_id` для получения дополнительных сведений для загрузки с помощью [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) , и [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) представления. Например, следующий запрос возвращает `run_id` и сведения о начала, окончания и длительность времени загрузки, а также все ошибки и количество строк, обработанных:  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id=’12738’;  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
