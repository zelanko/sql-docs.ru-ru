---
title: Функция SQLSetConnectInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5d8087e7672dd331d0b078cea4930be7582a026
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68092997"
---
# <a name="sqlsetconnectinfo-function"></a>Функция SQLSetConnectInfo
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 3,81 ODBC: интерфейс ODBC  
  
 **Сводка**  
 **SQLSetConnectInfo** используется для задания источника данных, идентификатор пользователя и пароль в info маркер подключения для приложения [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>Аргументы  
 *TokenHandle*  
 [Вход] Дескриптор маркера.  
  
 *ServerName*  
 [Вход] Имя источника данных. Данные могут быть расположены на одном компьютере с программой, или на другом компьютере, где-нибудь в сети. Сведения о выборе источника данных с помощью приложения, см. в разделе [Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Вход] Длина **ServerName* в символах.  
  
 *UserName*  
 [Вход] Идентификатор пользователя.  
  
 *NameLength2*  
 [Вход] Длина **UserName* в символах.  
  
 *Authentication*  
 [Вход] Строка для проверки подлинности (обычно пароль).  
  
 *NameLength3*  
 [Вход] Длина **проверки подлинности* в символах.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Совпадение с кодом [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) для входных данных ошибок проверки, за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обрабатывать** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку в приложение (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает значение SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получить диагностическую информацию от *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO для приложения в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
