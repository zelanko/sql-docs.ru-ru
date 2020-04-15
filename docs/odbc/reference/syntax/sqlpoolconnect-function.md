---
title: Функция S'LPoolConnect (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5045fe47683529f858b01e69f6af696e2821ca4c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306905"
---
# <a name="sqlpoolconnect-function"></a>Функция SQLPoolConnect
**Соответствия**  
 Версия Введена: СООТВЕТСТВИе стандартам ODBC 3.8: ODBC  
  
 **Сводка**  
 Для создания нового соединения используется **s-LPoolConnect,** если соединение в пуле не может быть использовано повторно.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbc*  
 (Вход) Ручка соединения.  
  
 *hDbcInfoToken*  
 (Вход) Ручка маркера для нового запроса на подключение приложения.  
  
 *wszOutConnectString*  
 (Выход) Указатель на буфер для завершенной строки соединения. При успешном подключении к целевому источнику данных этот буфер содержит завершенную строку соединения. Приложения должны выделять не менее 1024 символов для этого буфера.  
  
 Если *wszOutConnectString* является NULL, *cchConnectStringLen* будет по-прежнему возвращать общее количество символов (за исключением символа нулевого прекращения для данных о персонажах), доступных для возвращения в буфере, на который указывает *wszOutConnectString.*  
  
 *cchConnectStringBuffer*  
 (Вход) Длина буфера*wszOutConnectString* в символах.  
  
 *cchConnectStringLen*  
 (Выход) Указатель на буфер, в котором можно вернуть общее количество символов (за исключением символа нулевого прекращения), доступного для возврата в \* *wszOutConnectString.* Если количество символов, доступных для возврата, больше или равно *cchConnectStringBuffer,* завершенная строка соединения в \* *wszOutConnectString* усечена до *cchConnectStringBuffer* минус длина символа с нулевым прекращением.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or, SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 По аналогии с [S'LDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) для любой ошибки проверки ввода, за исключением того, что менеджер драйвера будет использовать **HandleType** SQL_HANDLE_DBC_INFO_TOKEN и **ручку** *hDbcInfoToken*.  
  
## <a name="remarks"></a>Remarks  
 Менеджер драйвера гарантирует, что материнская ручка *HENV hDbc* и *hDbcInfoToken* одинаковы.  
  
 В отличие от [S'LDriverConnect,](../../../odbc/reference/syntax/sqldriverconnect-function.md)нет аргумента *DriverCompletion,* чтобы побудить пользователей ввести информацию о подключении. Диалог запроса запрещен в сценарии объединения.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий объединение соединения с пониманием водителя, должен реализовать эту функцию.  
  
 Всякий раз, когда водитель возвращает SQL_ERROR или SQL_INVALID_HANDLE, менеджер драйвера возвращает ошибку в приложение (в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [S'LDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Всякий раз, когда водитель возвращается SQL_SUCCESS_WITH_INFO, менеджер драйвера получает диагностическую информацию от *hDbcInfoToken,* и возвращает SQL_SUCCESS_WITH_INFO в приложение в [S'LConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [S'LDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Когда приложение использует [S'LConnect,](../../../odbc/reference/syntax/sqlconnect-function.md) *wszOutConnectString* будет буфером NULL (последние три параметра будут установлены на NULL, 0, NULL). В противном случае драйвер должен вернуть строку вывода соединения, которая будет возвращена на вызов [функции SLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) приложения.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Пулинг соединения с информацией о драйверах](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
