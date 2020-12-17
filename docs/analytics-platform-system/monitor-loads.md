---
title: Отслеживание загрузок
description: Наблюдение за активностью и последней загрузкой с помощью консоли администрирования системы аналитики (ТД) или системных представлений параллельного хранилища данных (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b67460528da7cac2e7d3d2d10dfbb4719b08d77f
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97638073"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Мониторинг загрузки в хранилище Parallel Data
Мониторинг активных и недавних загрузок [dwloader](dwloader.md) с помощью консоли администрирования системы АНАЛИТИКИ (ТД) или [системных представлений](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)параллельного хранилища данных (PDW). 
  
> [!TIP]  
> Некоторые нагрузки инициируются с помощью инструкций INSERT или средств бизнес-аналитики, которые используют инструкции SQL для выполнения загрузки. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Предварительные требования  
Независимо от метода, используемого для отслеживания нагрузки, имя входа должно иметь разрешение на доступ к базовым источникам данных. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Мониторинг загрузок  
В следующих разделах описывается наблюдение за загрузкой.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Мониторинг нагрузок с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  В верхнем меню выберите пункт **загрузки**. Вы увидите таблицу с возможностью сортировки, в которой отображаются все последние и активные нагрузки, а также дополнительные сведения, например, завершена ли загрузка или она еще активна. Щелкните заголовки столбцов, чтобы отсортировать строки.  
  
3.  Чтобы просмотреть дополнительные сведения о конкретной нагрузке, щелкните **идентификатор** загрузки в левом столбце. В подробном представлении можно увидеть ход выполнения на каждом шаге загрузки.  
  
Сведения о метаданных нагрузки, отображаемых в консоли администрирования, см. в этих системных представлениях.  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md?view=aps-pdw-2016-au7&preserve-view=true)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Мониторинг загрузок с помощью системных представлений  
Чтобы отслеживать активные и последние загрузки с помощью SQL Server PDW представлений, выполните следующие действия. Сведения о столбцах и возможных значениях, возвращаемых представлением, для каждого используемого системного представления см. в документации по этому представлению.  
  
1.  Найдите `request_id` для загрузки в представлении [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) , найдя командную строку загрузчика в `command` столбце для этого представления.  
  
    Например, следующая команда возвращает текст команды и текущее состояние, а также `request_id` .  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Используйте `request_id` для получения дополнительных сведений о нагрузке с помощью [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) и [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) представлений. Например, следующий запрос возвращает `run_id` сведения о времени начала, окончания и продолжительности загрузки, а также все ошибки и сведения о количестве обработанных строк:  
  
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
