---
title: Мониторинг активных запросов (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb73f790-0537-414b-8dc2-f1eb69b92362
caps.latest.revision: 7
ms.openlocfilehash: 8a792e8dc4f29a257568f37350ba1b2c792c88fe
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="monitoring-active-queries"></a>Мониторинг активных запросов
В этом разделе показано, как использовать консоль администрирования и системных представлений SQL Server PDW для наблюдения за активных запросов. В разделе [отслеживать устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) и [системных представлений](tsql-system-views.md) сведения об этих средствах.  
  
## <a name="prerequisites"></a>предварительные требования  
Независимо от метода, который используется для наблюдения за активных запросов, пользователь, должен обладать разрешениями, описанными в «Использование всех из консоли администрирования» в [GRANT, предоставление разрешений для использования консоли администрирования](grant-permissions.md#grant-permissions-to-use-the-admin-console).  
  
## <a name="PermsAdminConsole"></a>Монитор активных запросов  
Для мониторинга активных запросов можно использовать консоль администрирования и системных представлений SQL Server PDW. Следуйте приведенным ниже инструкциям.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>Мониторинг активных запросов с помощью консоли администрирования  
  
1.  Войдите в консоль администрирования. В разделе [отслеживать устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md) инструкции.  
  
2.  В верхнем меню щелкните **запросы**. Появится таблица с основные сведения о последних запросов в устройстве, включая имя входа, который отправил запрос, время начала и окончания для запроса и текущее состояние запроса.  
  
3.  Чтобы увидеть команду запроса, наведите указатель мыши на идентификатор запроса в левом столбце для этой строки.  
  
    Для просмотра более подробных сведений для конкретного запроса, щелкните ИД запроса. Вы увидите сведения, включая полный запрос и план запроса с информацией о состоянии для каждого шага при выполнении запроса. Если были возвращены любые ошибки, можно также просмотреть подробную информацию об ошибках. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>Мониторинг активных запросов с помощью системных представлений  
Представление основной системы, используемое для отслеживания запросов является [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Используйте это системное представление для поиска `request_id` для активных или последних запросов, на основе текста запроса.  
  
Например, следующий запрос находит `request_id` и текущий `status` для любого запроса, который выбирает все столбцы из `memberAddresses` таблицы.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE ‘%SELECT * FROM db1..memberAddresses%’;  
```  
  
После `request_id` был определения запроса, используйте сведения в `dm_pdw_exec_requests` таблицы, чтобы узнать об обработке запроса или использовать [sys.dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) для просмотра состояния отдельного запроса действия для выполнения запроса.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
