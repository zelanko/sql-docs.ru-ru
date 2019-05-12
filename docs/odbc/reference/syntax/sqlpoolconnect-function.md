---
title: Функция SQLPoolConnect | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 297c856cc2481a6d3266d7654797f81b9b9f5c11
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536611"
---
# <a name="sqlpoolconnect-function"></a>Функция SQLPoolConnect
**Соответствие стандартам**  
 Представленные версии: ODBC 3.8 стандартов соответствия: интерфейс ODBC  
  
 **Сводка**  
 **SQLPoolConnect** используется для создания нового соединения, если нет подключения в пуле можно повторно использовать.  
  
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
 [Вход] Дескриптор соединения.  
  
 *hDbcInfoToken*  
 [Вход] Дескриптор маркера для нового запроса на подключение приложения.  
  
 *wszOutConnectString*  
 [Выход] Указатель на буфер для полную строку подключения. После успешного подключения к целевому источнику данных этот буфер содержит полную строку подключения. Приложения необходимо выделить по крайней мере 1 024 символов для данного буфера.  
  
 Если *wszOutConnectString* имеет значение NULL, *cchConnectStringLen* по-прежнему возвращает общее число символов (включая знак завершения null для символьных данных) для возврата в буфер, на которые указывают *wszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Вход] Длина **wszOutConnectString* буфера в символах.  
  
 *cchConnectStringLen*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число символов (за исключением знака завершения null) для возврата в \* *wszOutConnectString*. Если количество символов, доступных для возврата больше или равно *cchConnectStringBuffer*, завершения строку подключения в \* *wszOutConnectString* усекается до *cchConnectStringBuffer* минус длина знак завершения null.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Аналогичную [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) для любой входной ошибка проверки, за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обрабатывать** из *hDbcInfoToken*.  
  
## <a name="remarks"></a>Примечания  
 Диспетчер драйверов гарантирует, что родительский маркера HENV *hDbc* и *hDbcInfoToken* одинаковы.  
  
 В отличие от [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), существует не *DriverCompletion* аргумент предлагать пользователю ввести сведения о соединении. Диалоговое окно запроса не допускается в сценарии регулирования количества запросов.  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, диспетчер драйверов возвращает ошибку в приложение (в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) или [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Каждый раз, когда драйвер возвращает значение SQL_SUCCESS_WITH_INFO, диспетчер драйверов будет получить диагностическую информацию от *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO для приложения в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Если приложение использует [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *wszOutConnectString* будет пустой буфер (трех последних параметров все устанавливается в значение NULL, 0, NULL). В противном случае драйвер должен возвращать полученную строку подключения, которые будут возвращены в приложения [SQLDriverConnect, функция](../../../odbc/reference/syntax/sqldriverconnect-function.md) вызова.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
