---
title: Функция S'LSetConnectInfo (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b575e0d09f87ad21e1190b8081b6604349a98263
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301855"
---
# <a name="sqlsetconnectinfo-function"></a>Функция SQLSetConnectInfo
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.81: ODBC  
  
 **Сводка**  
 **Для** установки источника данных, идентификатора пользователя и пароля в токен информации о подключении для вызова [приложения sLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) используется для установки исходного кода данных, идентификатора пользователя.  
  
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
 *ТокенХэндлэнд*  
 (Вход) Ручка маркера.  
  
 *ServerName*  
 (Вход) Имя источника данных. Данные могут быть расположены на том же компьютере, что и программа, или на другом компьютере где-то в сети. Для получения информации о том, как приложение выбирает источник данных, [см.](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)  
  
 *NameLength1*  
 (Вход) Длина*сервера В* символах.  
  
 *Пользователя*  
 (Вход) Идентификатор пользователя.  
  
 *NameLength2*  
 (Вход) Длина*пользователя В* символах.  
  
 *Проверка подлинности*  
 (Вход) Строка аутентификации (обычно пароль).  
  
 *NameLength3*  
 (Вход) Длина*аутентификации* в персонажах.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Так же, как [и для](../../../odbc/reference/syntax/sqlconnect-function.md) ошибок ввода ввода, за исключением того, что менеджер драйвера будет использовать **HandleType** SQL_HANDLE_DBC_INFO_TOKEN и **ручку** *hDbcInfoToken*.  
  
## <a name="remarks"></a>Remarks  
 Всякий раз, когда водитель возвращает SQL_ERROR или SQL_INVALID_HANDLE, менеджер драйвера возвращает ошибку в приложение (в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [S'LDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Всякий раз, когда водитель возвращается SQL_SUCCESS_WITH_INFO, менеджер драйвера получает диагностическую информацию от *hDbcInfoToken,* и возвращает SQL_SUCCESS_WITH_INFO в приложение в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
