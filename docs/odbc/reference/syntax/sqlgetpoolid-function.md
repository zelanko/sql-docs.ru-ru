---
title: Функция SQLGetPoolID | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fc6737530fdf151573a570eb83f777785ddb679
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538080"
---
# <a name="sqlgetpoolid-function"></a>Функция SQLGetPoolID
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 3,81 ODBC: интерфейс ODBC  
  
 **Сводка**  
 **SQLGetPoolID** извлекает идентификатор пула.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbcInfoToken*  
 [Вход] Дескриптор токена, содержащий все сведения о соединении.  
  
 *pPoolID*  
 [Выход] Идентификатор пула, который используется для идентификации набора соединений, которые могут использоваться как взаимозаменяемые (возможно, требуется дополнительный сброса).  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetPoolID** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, диспетчер драйверов будут использовать **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обрабатывать** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Примечания  
 **SQLGetPoolID** позволяет получить идентификатор пула, исходя из набора сведений о соединении (из **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, и  **SQLSetConnectInfo**). Этот пул, идентификатор используется для идентификации набора подключений, которые могут использоваться как взаимозаменяемые (возможно, требуется дополнительный сброса). Идентификатор пула будет использоваться для идентификации пула подключений для этой группы подключений.  
  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку в приложение (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает значение SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получить диагностическую информацию от *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO для приложения в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
