---
title: Функция Склпулконнект | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306905"
---
# <a name="sqlpoolconnect-function"></a>Функция SQLPoolConnect
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,8: ODBC  
  
 **Сводка**  
 **Склпулконнект** используется для создания нового соединения, если не удается повторно использовать подключение в пуле.  
  
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
 *хдбк*  
 Входной Маркер подключения.  
  
 *хдбЦинфотокен*  
 Входной Маркер маркера для нового запроса на подключение приложения.  
  
 *всзаутконнектстринг*  
 Проверки Указатель на буфер для завершенной строки подключения. После успешного подключения к целевому источнику данных этот буфер содержит завершенную строку подключения. Для этого буфера приложения должны выделить не менее 1 024 символов.  
  
 Если *всзаутконнектстринг* имеет значение null, то *кчконнектстринглен* будет возвращать общее количество символов (исключая символ завершения null для символьных данных), доступный для возврата в буфер, на который указывает *всзаутконнектстринг*.  
  
 *кчконнектстрингбуффер*  
 Входной Длина буфера **всзаутконнектстринг* в символах.  
  
 *кчконнектстринглен*  
 Проверки Указатель на буфер, в котором возвращается общее число символов (за исключением символа завершения null), доступного для возврата в \* *всзаутконнектстринг*. Если число возвращаемых символов больше или равно значению *кчконнектстрингбуффер*, то завершенная строка подключения в \* *всзаутконнектстринг* усекается до *кчконнектстрингбуффер* за вычетом длины символа завершения null.  
  
## <a name="returns"></a>Результаты  
 SQL_INVALID_HANDLE, SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или.  
  
## <a name="diagnostics"></a>Диагностика  
 Аналогично [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) для любой ошибки проверки ввода, за исключением того, что диспетчер драйверов будет использовать **параметром handletype** SQL_HANDLE_DBC_INFO_TOKEN и **маркер** *хдбЦинфотокен*.  
  
## <a name="remarks"></a>Remarks  
 Диспетчер драйверов гарантирует, что родительский дескриптор ХЕНВ *хдбк* и *хдбЦинфотокен* одинаков.  
  
 В отличие от [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), отсутствует аргумент *DriverCompletion* , предлагающий пользователям вводить сведения о подключении. Диалоговое окно с приглашением не разрешено в сценарии объединения в пул.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий пулы соединений с учетом драйверов, должен реализовывать эту функцию.  
  
 Всякий раз, когда драйвер возвращает SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку приложению (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Всякий раз, когда драйвер возвращает SQL_SUCCESS_WITH_INFO, диспетчер драйверов получает диагностические сведения от *хдбЦинфотокен*и возвращает SQL_SUCCESS_WITH_INFO приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Если приложение использует [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *всзаутконнектстринг* будет пустым буфером (последние три параметра будут установлены в NULL, 0, null). В противном случае драйвер должен вернуть выходную строку подключения, которая будет возвращена в вызов [функции SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) приложения.  
  
 Включите склспи. h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйверов](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
