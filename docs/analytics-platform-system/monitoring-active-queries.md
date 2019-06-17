---
title: Мониторинг активных запросов — Parallel Data Warehouse | Документация Майкрософт
description: Используйте консоль администрирования и Parallel Data Warehouse системных представлений для мониторинга активных запросов в Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d2b1ee84b2ae738d7790e1238176331a221ac473
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62640007"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>Мониторинг активных запросов — Parallel Data Warehouse
В этой статье показано, как использовать консоль администрирования и системных представлений SQL Server PDW для мониторинга активных запросов. См. в разделе [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) и [системные представления](tsql-system-views.md) сведения об этих средствах.  
  
## <a name="prerequisites"></a>предварительные требования  
Независимо от того, метод, используемый для мониторинга активных запросов, имя входа должно иметь разрешения, описанные в «Используйте все из консоли администрирования» в [GRANT, предоставление разрешений для использования консоли администрирования](grant-permissions.md#grant-permissions-to-use-the-admin-console).  
  
## <a name="PermsAdminConsole"></a>Мониторинг активных запросов  
Мониторинг активных запросов можно использовать консоль администрирования и системных представлений SQL Server PDW. Выполните приведенные ниже инструкции.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>Мониторинг активных запросов с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. См. в разделе [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) инструкции.  
  
2.  В верхнем меню щелкните **запросы**. Вы увидите таблицу, содержащую основные сведения о последних запросов на устройстве, включая имя входа, который отправил запрос, время начала и окончания для запроса и текущее состояние запроса.  
  
3.  Чтобы увидеть команду запроса, наведите указатель мыши на идентификатор запроса в левом столбце для этой строки.  
  
    Чтобы просмотреть более подробные сведения для конкретного запроса, щелкните идентификатора запроса. Вы увидите сведения, включая полный запрос и план запроса, сведения о состоянии для каждого этапа выполнения запроса. Если возвращены все ошибки, можно также просмотреть подробную информацию об ошибках. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>Мониторинг активных запросов с помощью системных представлений  
Это представление основной системы используется для отслеживания запросов является [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Используйте это представление системы, чтобы найти `request_id` для активных или последних запросов, на основе текста запроса.  
  
Например, следующий запрос находит `request_id` и текущий `status` для любого запроса, который выбирает все столбцы из `memberAddresses` таблицы.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
После `request_id` был определения для запроса, используйте другие сведения в `dm_pdw_exec_requests` таблицы, чтобы узнать об обработке запроса либо использовать [sys.dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) для просмотра состояния отдельных запроса действия для выполнения запроса.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
