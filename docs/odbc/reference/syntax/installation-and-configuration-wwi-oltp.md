---
title: Функция SQLSetDriverConnectInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b886bdf5ce769201addacfdfe9e2f22c6e8a15d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706012"
---
# <a name="sqlsetdriverconnectinfo-function"></a>Функция SQLSetDriverConnectInfo
**Соответствие стандартам**  
 Версия была введена: ODBC 3,81 соответствие стандартам: ODBC  
  
 **Сводка**  
 **SQLSetDriverConnectInfo** используется для настройки строки подключения в info маркер подключения для приложения **SQLDriverConnect** вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Аргументы  
 *TokenHandle*  
 [Вход] Дескриптор маркера.  
  
 *InConnectionString*  
 [Вход] Строка подключения целиком (см. в разделе синтаксиса в «Комментарии» в [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), частичная строка подключения, или пустая строка.  
  
 *StringLength1*  
 [Вход] Длина **InConnectionString*, в символах, если строка Юникода или байтов, если строка ANSI или DBCS.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Совпадение с кодом [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) связанные с любой ошибки проверки входных данных, за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обрабатывать** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку в приложение (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает значение SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получить диагностическую информацию от *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO для приложения в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
