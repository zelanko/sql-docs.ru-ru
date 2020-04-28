---
title: Мониторинг активных запросов
description: Используйте консоль администрирования и системные представления параллельного хранилища данных для мониторинга активных запросов в системе платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 9157db745b999711966f0019747ba1d61823569e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400915"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>Мониторинг активных запросов — Параллельное хранилище данных
В этой статье показано, как использовать консоль администрирования и системные представления SQL Server PDW для наблюдения за активными запросами. Сведения об этих средствах см. в разделе [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) и [системных представлений](tsql-system-views.md) .  
  
## <a name="prerequisites"></a>Предварительные требования  
Независимо от метода, используемого для наблюдения за активными запросами, имя входа должно иметь разрешения, описанные в разделе "использование всей консоли администрирования" раздела [предоставление разрешений на использование консоли администрирования](grant-permissions.md#grant-permissions-to-use-the-admin-console).  
  
## <a name="monitor-active-queries"></a><a name="PermsAdminConsole"></a>Мониторинг активных запросов  
Для наблюдения за активными запросами можно использовать как консоль администрирования, так и системные представления SQL Server PDW. Выполните приведенные далее инструкции.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>Наблюдение за активными запросами с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. Инструкции см. в разделе [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) .  
  
2.  В верхнем меню щелкните **запросы**. Вы увидите таблицу с основными сведениями о последних запросах к устройству, включая имя входа, отправившего запрос, время начала и окончания запроса, а также текущее состояние запроса.  
  
3.  Чтобы увидеть команду запроса, наведите указатель мыши на идентификатор запроса в левом столбце для этой строки.  
  
    Чтобы просмотреть более подробные сведения о конкретном запросе, щелкните идентификатор запроса. Вы увидите сведения, включая полный запрос и план запроса, со сведениями о состоянии для каждого шага выполнения запроса. Если были возвращены какие бы то ни было ошибки, можно также просмотреть подробные сведения об этих ошибках. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>Наблюдение за активными запросами с помощью системных представлений  
Основное системное представление, используемое для отслеживания запросов, — [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Используйте это системное представление для поиска `request_id` активного или последнего запроса на основе текста запроса.  
  
Например, следующий запрос находит `request_id` и текущий `status` запрос для любого запроса, выбирающего все столбцы из `memberAddresses` таблицы.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
`request_id` После определения запроса используйте другие сведения в `dm_pdw_exec_requests` таблице, чтобы узнать об обработке запроса, или используйте [sys. dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) , чтобы просмотреть состояние отдельных шагов запроса для выполнения запроса.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
