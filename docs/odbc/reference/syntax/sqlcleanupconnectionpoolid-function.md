---
title: Функция SQLCleanupConnectionPoolID | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4d00fcff0b2fa1948f6b2f6f66b863501e12d97
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537699"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>Функция SQLCleanupConnectionPoolID
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 3,81 ODBC: интерфейс ODBC  
  
 **Сводка**  
 **SQLCleanupConnectionPoolID** информирует драйвер, истекло время ожидания идентификатор пула. Истекло время ожидания пула, идентификатор может времени ожидания, каждый раз, когда были все соединения в пул, связанный с таким Идентификатором пула. См. в разделе [пула в Microsoft Data Access Components](https://msdn.microsoft.com/library/ms810829.aspx) Дополнительные сведения о времени ожидания соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *EnvironmentHandle*  
 [Вход] Дескриптора среды пула.  
  
 *PoolID*  
 [Вход] Пул, связанный идентификатору пула, которое было превышено время ожидания.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Диспетчер драйверов не будет обрабатывать диагностические сведения, возвращенные из **SQLCleanupConnectionPoolID**.  
  
 Приложение не может получить сообщение об ошибке, возвращаемую драйвером.  
  
## <a name="remarks"></a>Примечания  
 **SQLCleanupConnectionPoolID** можно вызвать в любое время, но диспетчер драйверов гарантирует, что ни один поток одновременно вызывает **SQLGetPoolID** и ни один поток одновременно вызывает  **SQLRateConnection** и **SQLPoolConnect** с маркером сведения соединения, присвоены значения с помощью этого идентификатора пула. Таким образом драйвер необходимо убедиться в том, что эта функция является потокобезопасным.  
  
 Драйвер можно очистить ресурсы, связанные с идентификатором пула.  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
