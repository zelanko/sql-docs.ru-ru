---
title: Функция SQLPoolConnect | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 130c39d4aab986b5053192d2fe2c548e89ccef2e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlpoolconnect-function"></a>Функция SQLPoolConnect
**Соответствия**  
 Появился в версии: ODBC 3.8 нормативных требований: ODBC  
  
 **Сводка**  
 **SQLPoolConnect** используется для создания нового соединения, если нет соединения в пуле может быть повторно использован.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbc*  
 [Вход] Дескриптор соединения.  
  
 *hDbcInfoToken*  
 [Вход] Дескриптор токена для нового запроса подключения приложения.  
  
 *wszOutConnectString*  
 [Выход] Указатель на буфер для полную строку подключения. После успешного подключения к целевому источнику данных этот буфер содержит полную строку подключения. Приложения, необходимо выделить по крайней мере 1 024 символов для этого буфера.  
  
 Если *wszOutConnectString* имеет значение NULL, *cchConnectStringLen* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфер, на который указывает *wszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Вход] Длина **wszOutConnectString* буфера в символах.  
  
 *cchConnectStringLen*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением знака завершения null) для возврата в \* *wszOutConnectString*. Если количество символов вернуть больше или равно *cchConnectStringBuffer*, выполнить строку подключения в \* *wszOutConnectString* усекается до *cchConnectStringBuffer* за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Аналогично [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) для любых входных об ошибке проверки, за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обработки** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Замечания  
 Диспетчер драйверов гарантирует, что родительский HENV handle *hDbc* и *hDbcInfoToken* совпадают.  
  
 В отличие от [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), имеется не *DriverCompletion* аргумент Предлагайте пользователям вводить сведения о соединении. Диалоговое окно запросов запрещена в сценарии регулирования количества запросов.  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Всякий раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает приложению ошибку (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получать диагностические данные из *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO к приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Если приложение использует [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *wszOutConnectString* будет пустой буфер (последние три параметра будет все установлено значение NULL, 0, NULL). В противном случае драйвер должен возвращать строке подключения выходные данные возвращаются в приложения [SQLDriverConnect, функция](../../../odbc/reference/syntax/sqldriverconnect-function.md) вызова.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
