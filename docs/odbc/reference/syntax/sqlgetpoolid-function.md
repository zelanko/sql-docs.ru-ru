---
title: "Функция SQLGetPoolID | Документы Microsoft"
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
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8db01749cf58e34c59294367b3e24105906b635
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetpoolid-function"></a>Функция SQLGetPoolID
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 3,81 ODBC: ODBC  
  
 **Сводка**  
 **SQLGetPoolID** извлекает идентификатор пула.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbcInfoToken*  
 [Вход] Дескриптор токена, содержащий все сведения о соединении.  
  
 *pPoolID*  
 [Выход] Идентификатор пула, который используется для идентификации набора подключений, которые могут быть взаимозаменяемыми (возможно, требуется дополнительный сброса).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetPoolID** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, диспетчер драйверов будут использовать **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обработки** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Замечания  
 **SQLGetPoolID** используется для получения идентификатора пула, исходя из набора сведений о соединении (из **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, и  **SQLSetConnectInfo**). Этот идентификатор используется для идентификации набора подключений, которые могут быть взаимозаменяемыми пул (возможно, требуется дополнительный сброса). Идентификатор пула будет использоваться для идентификации пула соединений для этой группы подключений.  
  
 Всякий раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает приложению ошибку (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получать диагностические данные из *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO к приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC, поддерживающие пула соединений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

