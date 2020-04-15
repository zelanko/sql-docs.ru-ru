---
title: Функция S'LSetDriverConnectInfo (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10336475e39598161126c13771ad822de0d5f7d8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298807"
---
# <a name="sqlsetdriverconnectinfo-function"></a>Функция SQLSetDriverConnectInfo
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **Для** установки строки соединения в токен информации о подключении для вызова **приложения S'LDriverConnect** используется для установки строки соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Аргументы  
 *ТокенХэндлэнд*  
 (Вход) Ручка маркера.  
  
 *InConnectionString*  
 (Вход) Строка полного подключения (см. синтаксис в "Комментарии" в [S'LDriverConnect),](../../../odbc/reference/syntax/sqldriverconnect-function.md)частичная строка соединения, или пустая строка.  
  
 *Струннаядлина1*  
 (Вход) Длина*InConnectionString*, в символах, если строка Unicode, или байты, если строка ANSI или DBCS.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Так же, как [и s'LDriverConnect,](../../../odbc/reference/syntax/sqldriverconnect-function.md) связанный с любой ошибкой проверки ввода, за исключением того, что менеджер драйвера будет использовать **HandleType** SQL_HANDLE_DBC_INFO_TOKEN и **ручку** *hDbcInfoToken*.  
  
## <a name="remarks"></a>Remarks  
 Всякий раз, когда водитель возвращает SQL_ERROR или SQL_INVALID_HANDLE, менеджер драйвера возвращает ошибку в приложение (в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [S'LDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Всякий раз, когда водитель возвращается SQL_SUCCESS_WITH_INFO, менеджер драйвера получает диагностическую информацию от *hDbcInfoToken,* и возвращает SQL_SUCCESS_WITH_INFO в приложение в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
