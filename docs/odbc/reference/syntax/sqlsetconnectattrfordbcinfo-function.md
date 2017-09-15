---
title: "Функция SQLSetConnectAttrForDbcInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3ffe1bf224a28d7ff1151033576abcd5f10f56ed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>Функция SQLSetConnectAttrForDbcInfo
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 3,81 ODBC: ODBC  
  
 **Сводка**  
 **SQLSetConnectAttrForDbcInfo** совпадает со значением **SQLSetConnectAttr**, но он задает атрибут на маркер сведения подключения вместо на дескриптор соединения.  
  
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
 [Вход] Дескриптор токена.  
  
 *Attribute*  
 [Вход] Атрибут. Список доступных атрибутов является драйвера и аналогичны [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Вход] Указатель на значение должны быть связаны с *атрибут*. В зависимости от значения *атрибута*, *ValuePtr* будет значение 32-разрядное целое число без знака или будет указывать строку, завершающуюся значением null. Обратите внимание, что если *атрибута* аргумент представляет собой значение драйвера, значение в *ValuePtr* может быть целое число со знаком.  
  
 *StringLength*  
 [Вход] Если *атрибута* является атрибутом, определенных для ODBC и *ValuePtr* указывает на строку символов или двоичных буфера, данный аргумент должен иметь длину **ValuePtr*. Для символьных строковых данных этот аргумент должен содержать число байтов в строку.  
  
 Если *атрибута* является атрибутом, определенных для ODBC и *ValuePtr* является целым числом, *StringLength* учитывается.  
  
 Если *атрибута* является атрибутом, определяемым драйвером, приложение сможет определить природу атрибут диспетчера драйверов, задав *StringLength* аргумент. *StringLength* может иметь следующие значения:  
  
-   Если *ValuePtr* является указателем на строку символов, затем *StringLength* длина строки или SQL_NTS.  
  
-   Если *ValuePtr* — это указатель на двоичные буфер, то приложение помещает результат SQL_LEN_BINARY_ATTR (*длина*) макрос в *StringLength*. В этом случае отрицательное значение в *StringLength*.  
  
-   Если *ValuePtr* — это указатель на значение, отличное от строки символов или двоичная строка затем *StringLength* должно иметь значение SQL_IS_POINTER.  
  
-   Если *ValuePtr* содержит значение фиксированной длины, то *StringLength* — SQL_IS_INTEGER или SQL_IS_UINTEGER, соответствующим образом.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 То же, что [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), за исключением того, что будет использоваться диспетчер драйверов **HandleType** из SQL_HANDLE_DBC_INFO_TOKEN и **обработки** из *hDbcInfoToken *.  
  
## <a name="remarks"></a>Замечания  
 **SQLSetConnectAttrForDbcInfo** совпадает со значением **SQLSetConnectAttr**, но задает атрибут на маркер сведения соединения вместо на дескриптор соединения. Например если **SQLSetConnectAttr** не распознает атрибут **SQLSetConnectAttrForDbcInfo** также вернет значение SQL_ERROR для этого атрибута.  
  
 Каждый раз, когда драйвер возвращает значение SQL_ERROR или SQL_INVALID_HANDLE, драйвер должен игнорировать этот атрибут для вычисления код пула. Кроме того, диспетчер драйверов будет получать диагностические данные из *hDbcInfoToken*и возвращают значение SQL_SUCCESS_WITH_INFO к приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Таким образом приложение может получить сведения о том, почему некоторые атрибуты нельзя устанавливать.  
  
 Приложения не должны напрямую вызывать эту функцию. Драйвер ODBC, который поддерживает пулы соединений с учетом драйвера необходимо реализовать эту функцию.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйвера](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC, поддерживающие пула соединений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
