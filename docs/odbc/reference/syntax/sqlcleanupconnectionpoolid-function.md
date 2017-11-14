---
title: "Функция SQLCleanupConnectionPoolID | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 49d204d7d77ae39c6a7eb3c9d408f6d72bafcc91
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcleanupconnectionpoolid-function"></a>Функция SQLCleanupConnectionPoolID
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 3,81 ODBC: ODBC  
  
 **Сводка**  
 **SQLCleanupConnectionPoolID** уведомляет драйвер, истекло время ожидания идентификатор пула. Истекло время ожидания пула, код может время ожидания всякий раз, когда были все соединения в пул, связанный с указанным Идентификатором пула. В разделе [пула в Microsoft Data Access Components](http://msdn.microsoft.com/library/ms810829.aspx) Дополнительные сведения о времени ожидания соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *EnvironmentHandle*  
 [Вход] Дескриптор пула.  
  
 *PoolID*  
 [Вход] Пул, связанный идентификатор пула, истекло.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Диспетчер драйверов не будет обрабатывать диагностических сведений, возвращаемых из **SQLCleanupConnectionPoolID**.  
  
 Приложение не может получить сообщение об ошибке, возвращаемую драйвером.  
  
## <a name="remarks"></a>Замечания  
 **SQLCleanupConnectionPoolID** можно вызвать в любое время, но диспетчер драйверов гарантирует, что ни один поток одновременно вызов **SQLGetPoolID** и ни один поток одновременно вызов  **SQLRateConnection** и **SQLPoolConnect** с маркером сведения соединения с этим идентификатором пула. Таким образом драйвер должен убедитесь, что эта функция является потокобезопасным.  
  
 Драйвер можно очистить ресурсы, связанные с идентификатором пула.  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC, поддерживающие пула соединений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

