---
title: Функция SQLSetConnectAttrForDbcInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 798f986adfeda95ef091161458d94c2ccc33b2e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63125538"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>Функция SQLSetConnectAttrForDbcInfo
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 3,81 ODBC: интерфейс ODBC  
  
 **Сводка**  
 **SQLSetConnectAttrForDbcInfo** совпадает со значением **SQLSetConnectAttr**, но он задает атрибут в маркере сведения соединения вместо на дескриптор соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Аргументы  
 *hDbcInfoToken*  
 [Вход] Дескриптор маркера.  
  
 *Attribute*  
 [Вход] Атрибут. Список допустимых атрибутов — это драйвер и так же, как [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Вход] Указатель на значение, которым будет связана *атрибут*. В зависимости от значения *атрибут*, *ValuePtr* будет представлять собой значение 32-разрядного целого числа без знака или указывает на строку символов с завершающим нулем. Обратите внимание, что если *атрибут* аргумент представляет собой значение конкретного драйвера, значение в *ValuePtr* может быть целое число со знаком.  
  
 *StringLength*  
 [Вход] Если *атрибут* является атрибутом, определенных для ODBC и *ValuePtr* указывает на строку символов или двоичный буфер, данный аргумент должен иметь длину **ValuePtr*. Для строки символьных данных этот аргумент должен содержать число байтов в строке.  
  
 Если *атрибут* является атрибутом, определенных для ODBC и *ValuePtr* должно быть целым числом, *StringLength* учитывается.  
  
 Если *атрибут* является атрибутом, определяемым драйвером, приложение указывает характер атрибут для диспетчера драйверов, задав *StringLength* аргумент. *StringLength* может иметь следующие значения:  
  
-   Если *ValuePtr* — это указатель на строку символов, затем *StringLength* длина строки или SQL_NTS.  
  
-   Если *ValuePtr* является указателем в двоичный буфер, а затем приложение размещает результат SQL_LEN_BINARY_ATTR (*длина*) в макрос *StringLength*. Это размещает отрицательное значение в *StringLength*.  
  
-   Если *ValuePtr* — это указатель на значение, отличное от строку символов или двоичная строка, затем *StringLength* должно иметь значение SQL_IS_POINTER.  
  
-   Если *ValuePtr* содержит значение фиксированной длины, то *StringLength* является SQL_IS_INTEGER или SQL_IS_UINTEGER, соответствующим образом.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Совпадение с кодом [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обрабатывать** из *hDbcInfoToken* .  
  
## <a name="remarks"></a>Примечания  
 **SQLSetConnectAttrForDbcInfo** совпадает со значением **SQLSetConnectAttr**, но он задает атрибут в маркере сведения соединения вместо на дескриптор соединения. Например если **SQLSetConnectAttr** не распознает атрибут, **SQLSetConnectAttrForDbcInfo** также вернет значение SQL_ERROR для этого атрибута.  
  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, драйвер должен игнорировать этот атрибут для вычисления идентификатор пула. Кроме того, диспетчер драйверов будет получить диагностическую информацию от *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO для приложения в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Таким образом приложение может получать сведения о почему некоторые атрибуты нельзя устанавливать.  
  
 Приложения не эту функцию следует вызывать напрямую. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
